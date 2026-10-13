# 12 · When something's off

*Croo Operator's Manual · v1.0 · 2026-10-12*

**The one thing to know: your first move is always the same — describe
what you see to Nova, in plain words.** Not the technical cause, not a
guess at the fix. "Jack's pane went blank after I sent a file" is a
perfect report; Nova takes it from there.

## Nova first

Nova is the custodian: diagnosing the installation is her job. She can
look at what's running, check the health of the pieces, and either fix
it or tell you plainly what she found. Most "something's off" moments
end here, in a minute, without you learning anything about logs — which
is the point.

What helps her most:

- **What you saw**, in your words. What you clicked, what happened,
  what you expected instead.
- **When it started.** "Since this morning" narrows more than it
  sounds like it would.
- **A screenshot**, if it's visual.

## The bug report

Found something genuinely broken? Ask Nova to write it up:

> "Nova, write up a bug report on that — I want to send it in."

She produces a proper report — what happened, versions, the details
that matter — without you gathering any of it. Paste it into the
feedback form along with anything you'd add in your own words. Reports
land directly with the engineering team and shape what gets fixed
first; during the beta, this is genuinely the most valuable thing you
can send us.

And privacy stays the rule it always was: nothing leaves your machine
unless you see it and send it.

## If the workspace itself won't load

The one case Nova-in-the-chat can't help with is the chat not loading.
But Nova herself is still running — only the workspace in front of her
is down. Three moves, in order:

1. **Reach Nova in the terminal.** Open a terminal and type
   `croo attach nova` — you're now talking to Nova directly, same
   agent, same memory, just without the workspace around her. Tell her
   the workspace won't load and let her fix it. When you're done, press
   Ctrl-b and then d to step back out — closing the window other ways
   can disturb her session.
2. **The terminal, for emergencies** — if even Nova is unreachable,
   type `croo help`: the first thing it prints is an emergency
   procedure for exactly this case, step by step. The commands worth
   knowing are below, and cli.md walks through all of them in full.
3. **support.md** — if neither works, this is the path to us: what to
   collect, where to send it, what to expect back.

### The commands worth knowing

A workspace outage does not normally stop your agents — they keep
running underneath. These commands let you see that, and put things
back. The first four only look; they are safe to run any time, even
out of curiosity.

- **`croo access`** — the first question, answered: is the workspace
  actually down, or just your browser tab? It checks the service and
  prints the address to open.
- **`croo ls`** and **`croo status`** — who's running and what state
  each agent is in. This is how you confirm the crew is fine even
  while the workspace isn't.
- **`croo doctor`** — a health check on Croo's own records: it audits
  every agent's registration and conversation link and tells you what
  it found. On its own it is read-only — it diagnoses and advises,
  and changes nothing until you ask it to.
- **`croo attach <name>`** — work directly with any agent, Nova
  included, exactly as in move 1. Leave with Ctrl-b, then d.
- **`croo stop <name>`** and **`croo start <name>`** — pause an agent
  and bring it back later, same conversation, same memory. Stop is
  the gentle option: nothing is lost.
- **`croo respawn`** — after a reboot: brings every registered agent
  back, each resuming its own conversation. The order that works:
  `doctor` first, fix anything it advises, then `respawn`.
- **`croo session recover <name>`** — for the rare case where Croo
  found an agent's conversation but refused to resume it without you;
  this is you saying "go ahead", deliberately.

Each command explains itself with `--help`, and `croo help` shows the
full list. None of them installs, deletes or sends anything — the
terminal here is a recovery room, not a second workspace.

## Habits that pay

- **Report the weird, not just the broken.** Something that "felt
  off" but recovered is exactly the kind of thing a beta wants to
  hear about.
- **One report per thing.** Three issues in one report get one
  muddled fix. (The same rule as briefs, chapter 4 — it's all
  briefing.)
- **Let Nova do the gathering.** A two-line description plus her
  report beats twenty minutes of your own detective work, every time.

Inside Croo? Just ask Nova. (Even for this chapter — especially for
this chapter.)
