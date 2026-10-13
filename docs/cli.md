# The terminal, for emergencies  (DRAFT 1, 2026-10-12)

*Croo Docs · 2026-10-12*

Day to day, you never need a terminal: Nova and the workspace are the
whole interface. This page is for the three days that's not true —
**the workspace won't load**, **the machine rebooted**, or **an agent
is waiting on you to recover it**. Everything here is safe to read
ahead of time and designed to be followed under stress.

Two things to hold onto before any command:

- **Your agents are almost certainly fine.** A workspace outage doesn't
  stop them — they keep running underneath. The commands below mostly
  just let you see that, and switch things back on.
- **Nothing here acts without asking.** Every command that changes
  anything explains itself and waits for your yes. Add `-y` only when
  you've read what a command will do and want it to proceed unprompted.

## Opening the terminal

Open the Terminal app and type `croo help`. Two useful things happen:
you get the full command list, and the first block it prints is an
emergency procedure with the exact folder your Croo lives in. If plain
`croo` isn't recognised, `cd` into that folder and use `./bin/croo`
instead — same commands, written as `./bin/croo status` and so on.

## Story one: the workspace won't load

First, remember chapter 12 of the manual: **if Nova is up, you don't
need the rest of this page.** Check with `croo ls` — if Nova's row
shows her alive, run `croo attach nova`, tell her the workspace won't
load, and let her do the repair. (Leave her terminal with **Ctrl-b,
then d** — not Ctrl-c, not closing the window.)

Doing it by hand is the same repair:

1. `croo access` — is it actually down? If this prints a healthy
   address, Croo is fine; open that address fresh. The problem was the
   browser tab, not Croo.
2. If it's down: `croo web status`, then `croo web start -y`. If
   status says it's running but it still won't load, `croo web restart
   -y` — this touches only the workspace service; agent conversations
   are never affected. One wait worth knowing: if `croo web status`
   says automatic recovery is armed, give it two minutes to fix itself
   before forcing anything.
3. `croo access` again — healthy address, open it, done.

If `croo` itself won't run at all, use the emergency block from
`croo help` on another machine or from memory: go to your Croo folder,
start an installed coding agent (`claude` or `codex`), and tell it:
*"Read croo-recovery.md and get croo-web back up."* That file ships
with every Croo for exactly this moment.

## Story two: the machine rebooted

After a reboot, nothing comes back by itself — and the order matters:

1. `croo web start -y` — the workspace service first. (Restoring
   agents does *not* start it, so this step is never skippable.)
2. `croo doctor` — a read-only health check of Croo's records. If it
   advises a fix, `croo doctor --fix` applies only what it's confident
   about, and asks first.
3. `croo respawn` — brings every agent back, each resuming its own
   conversation. An agent whose conversation can't be safely found is
   left stopped with an alert — never silently restarted blank.
4. `croo ls` — confirm the crew. Nova is down like everyone else until
   this point; once her row shows alive, she can take over anything
   that's left. Any row saying **"awaiting operator recovery"** —
   that's story three.

## Story three: "awaiting operator recovery"

Sometimes Croo finds an agent's conversation but won't resume it
without you — that refusal is deliberate, because resuming the wrong
conversation is worse than waiting. You decide, with evidence:

1. `croo session status` — which agents can resume, and which wait.
2. `croo session verify <name>` — a read-only preview of the evidence
   for that agent's conversation.
3. `croo session recover <name>` — shows you what it found, then
   `croo session recover <name> --accept` if the conversation shown is
   genuinely that agent's, or `--reject` if it isn't. Plain `recover`
   never launches anything on its own.

The last resort, only when a conversation is truly gone and you've
decided to accept that: `croo start <name> --fresh` starts the agent
on a **new, empty conversation** — same name, profile, engine and
model, but yesterday's conversation is not coming back. Croo will ask
before doing it.

## The commands, in one place

| | |
|---|---|
| `croo help` | The full list, starting with the emergency procedure. `croo help <command>` explains any one of them. |
| `croo access` | Is the workspace up? Prints the address and health. |
| `croo ls` / `croo status` | Every agent and its state / a one-line summary. Works even with the workspace down. |
| `croo attach <name>` | That agent's own terminal, workspace not needed. Leave with Ctrl-b, then d. |
| `croo doctor` | Read-only audit of Croo's records; advises, changes nothing until you ask. |
| `croo web status / start -y / restart -y` | The workspace service itself. Restart touches only the service, never agents. |
| `croo stop <name>` / `croo start <name>` | Pause an agent and bring it back — same conversation, nothing lost. |
| `croo respawn` | After a reboot: every agent back, each on its own conversation. Doesn't start the workspace — do that first. |
| `croo heal` | One recovery pass for an agent that died unexpectedly while the workspace is up. Croo doesn't run this for you — if a tile has gone dark, it's yours to run. |
| `croo session status / verify / recover` | The "awaiting operator recovery" path — story three. |

Anything not on this page isn't emergency equipment — it's Nova's
day-job tooling, and a few of those verbs can discard a conversation
if used casually. When in doubt: attach Nova and ask, rather than
experimenting in the terminal.

## If none of this worked

That's what support is for — see [support.md](support.md): what to
collect, where to send it, and what to expect back. Collecting takes
minutes, and nothing in this situation gets worse by waiting.

Back inside Croo? Then the terminal's job is done. Just ask Nova.
