# Authoring guide — building for the croo playground

The **playground** tab on croo-web's bottom bar opens a small menu of pages
that run right inside croo: a game for a break, a tool you use every day, a
toy, a dashboard, a quiz, anything that fits in one HTML file. Every page can
also ask the machine's **local AI** for text, when the operator has one
running.

A page is one self-contained `.html` file. There is no build step, nothing to
register on the server and no restart: drop the file in the right folder and
reload the page.

## Where your pages go

| Folder | Whose | What shows in the playground |
|---|---|---|
| `var/games/` | **yours** | every `.html` in it, automatically |
| `web/games/` | croo's | the pages croo ships, as listed in its `enabled.json` |

**Put your pages in `var/games/`.** That folder is yours: no install or update
ever touches it, and a page there appears in the playground by itself. If you
give your page the same filename as one croo ships, yours wins.

Don't add pages to `web/games/`. It is part of croo's release, and the next
update replaces it, your page included. (The folder names still say "games"
because that is what the playground started as; they work the same for any
page.)

## The contract — what makes a file a playground page

1. **One self-contained `.html` file**, directly in the folder (subfolders are
   not scanned). Inline your CSS and script. Images can be inlined as data URIs
   or sit beside the page as `.png` / `.jpg` / `.webp` files in the same folder,
   referenced by filename.

2. **A title:** `<meta name="croo-game" content="Display Name">` in the
   `<head>`, within the first 4 KB of the file. That is the name the menu
   shows. Without it the page still lists, titled by its filename.

3. **Let the person leave:** on **Esc**, post
   `window.parent.postMessage({ type: 'croo-game-exit' }, '*')` so croo closes
   the overlay. The simplest way to get this right is to copy the
   `CROO-GAME CONTRACT BOILERPLATE` block from any page croo ships in
   `web/games/`: it wires the Esc exit, high-DPI canvas sizing,
   pause-when-hidden, and key handling that only claims the page's own keys
   (never Tab / Cmd / Ctrl / Alt). A page that is not a canvas game can keep
   just the Esc part.

4. **Fill the viewport** (`100vw × 100dvh`), use a dark background, and make
   **no network requests of any kind.** A page runs inside a locked-down
   `sandbox="allow-scripts"` frame, so every `fetch()` fails. The one way out
   is the local AI, below, which works by messaging croo rather than making a
   request.

## Using the local AI

Any page can ask croo's local AI for a short completion: hints, flavour text,
a summary, a rewrite, a riddle, an explanation, procedural content, whatever
your page needs. The operator decides whether a local AI is running; your page
finds out and adapts.

### How it works: messaging, not `fetch`

A page runs with an *opaque* origin (literally `"null"`): no same-origin
access, no cookies, no stored credentials, and the browser refuses `fetch()`
to anything, a local model included. So a page never talks to a model
directly. It talks to its **parent window**, croo-web, and croo makes the
request from the server side:

```
your page  --postMessage-->  croo-web  --(server-side request)-->  local AI
           <--postMessage--            <----------
```

Nothing to configure and no browser permissions. It also means the model is
only reachable *through* croo, never opened up to arbitrary web pages.

### Messages you send (page → croo)

Post to `window.parent` with `targetOrigin` `'*'`:

```js
// Ask what's available. `id` is optional; it is echoed back if you send one.
parent.postMessage({ type: 'croo-ai-probe', v: 1, id: 'p1' }, '*');

// Ask for a completion.
parent.postMessage({ type: 'croo-ai-request', v: 1, id: 'q7',
                     prompt: 'Two words for a cat.', maxTokens: 64 }, '*');
```

### Messages you receive (croo → page)

```js
window.addEventListener('message', (e) => {
  const d = e.data;
  if (!d || typeof d !== 'object') return;

  if (d.type === 'croo-ai-caps') {
    // d.available (bool), d.model (string|null), d.id (echo, or null if unsolicited)
  }
  if (d.type === 'croo-ai-result') {
    // d.id matches your request
    // d.ok === true  → d.text (string), d.model (string|null)
    // d.ok === false → d.reason (see the table below)
  }
});
```

### The five reasons, the whole vocabulary

| `reason` | Means | What the page should do |
|---|---|---|
| `unavailable` | No local AI. The operator has it off, picked a non-local one, or it isn't reachable. | Hide the AI feature. This answer is authoritative. |
| `error` | Something failed and it says nothing about the model (an empty prompt, a bad reply, croo-web mid-restart). | Retry or show a soft failure. **Never** hide the feature on this. |
| `timeout` | The model took longer than 20 seconds. | Offer a retry. |
| `busy` | Another request is already in flight. One at a time. | Wait and retry; don't queue a pile of requests. |
| `too_long` | `prompt` over 2000 chars, or `maxTokens` over 512. | Fix the request: this is a bug in the page, not the operator's setup. |

Treat any reason you don't recognise as `error`, the safe one.

### Rules that will bite you if you skip them

1. **`available: true` means CONFIGURED, not ALIVE.** It says a local backend
   is *selected*, not that it is currently answering. So when the person opens
   an AI feature, fire a warm-up (a throwaway prompt with `maxTokens: 1`) and
   let the response, or its absence, tell you whether the model is cold,
   alive, or gone.

2. **Capability updates arrive unsolicited, so listen for them.** croo pushes a
   `croo-ai-caps` message (with `id: null`) whenever availability or the model
   changes. Handle that push, or your page stays dark after the operator turns
   the AI back on.

3. **One request at a time.** A second concurrent request gets `busy`; it does
   not queue.

4. **The ceilings are hard numbers.** `prompt` ≤ 2000 chars, `maxTokens` ≤ 512,
   20-second timeout. Over a ceiling is `too_long`, never a silent truncation.

5. **There is no system prompt.** Your `prompt` is the entire input; nothing
   is prepended. Put any persona or format instruction in the text you send.

6. **Sanitise what comes back.** `d.text` is raw model output: never
   `innerHTML` it. Use `textContent`, or your own parser.

7. **Closing the page drops in-flight answers.** A reply that arrives after
   the person exits is not delivered to the next page.

8. **AI-off always wins.** Pages get only a *local* backend, and nothing at
   all when the operator has AI switched off.

## Adding, hiding, changing — your own pages

| You want to… | Do this | Result |
|---|---|---|
| **Add** a page | save `Name.html` in `var/games/` | appears in the playground on next open |
| **Change** a page | edit the file in place | served fresh on reload |
| **Rename** it in the menu | edit its `<meta name="croo-game">` | new title on next open |
| **Take it out** | move it out of `var/games/` (or into a subfolder) | gone from the menu |
| **Replace** a page croo ships | save yours under the same filename | yours is shown instead |

Subfolders are never scanned or served, so a half-finished page can wait in
`var/games/wip/` until it is ready.

## Pages croo ships (`web/games/`)

This part is for whoever curates croo's own release. croo's pages are listed
by `web/games/enabled.json`, a plain JSON array of filenames; only files named
in it are offered, so an unfinished page can sit in the folder without showing.
A missing or corrupt `enabled.json` offers *every* `.html` in the folder (a
typo can never empty the menu); a valid empty list `[]` offers none. It is
read fresh on every menu open. Which pages actually ship to customers is
decided at release time, not by this file.
