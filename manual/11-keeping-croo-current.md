# 11 · Keeping Croo current

*Croo Operator's Manual · v1.0.1 · 2026-10-13*

**The one thing to know: nothing updates itself.** Croo tells you when
something has an update, you prepare it from the workspace, and
nothing applies without your confirmation. Up to date is a choice you
make, not something that happens to you.

**Current is the healthy state.** The engines move quickly — new
models, new features, new behaviour, sometimes week to week — and
each Croo release is built and tested against the engines *as they
are now*. When an engine changes how it works, Croo changes with it;
applying both sides promptly is what keeps that pairing smooth. Fall
a few versions behind and things will mostly still work — but the
newest models won't be in your menus, features Croo already supports
sit unused, and you're running a combination nobody is testing
anymore. So when the Updates view shows something, plan to apply it
at the next natural pause — this sitting or the next, not next month.

## The Updates view

One place in the menu shows what could be newer: Croo itself, and the
engines your agents run on. When something has an update, you'll see
it there — what it is, and what applying it involves. No nagging, no
countdown, no silent installs.

## Updating an engine

Engines (Claude, Codex, AGY, Grok) publish their own updates, and Croo
manages the awkward part for you: a running agent keeps the engine
version it started with, so an engine update only fully lands when the
agent restarts. Croo handles that safely — agents are brought to the
new version when they're idle, never mid-job, and each one resumes its
own conversation afterwards. You confirm; Croo sequences.

If an agent is mid-way through something long, there's no urgency:
"restart to finish the update" can wait until the work doesn't.

## Updating Croo

New Croo releases are announced — during the beta, through the channel
your invitation set up. When one is out, ask Nova: applying a release
is a job she does with you, with your confirmation at the step that
matters, and a health check at the end. The update doc that travels
with each release (update.md) is the by-hand version of the same
steps — you'll likely never need it, but it's there, and it's the
recovery path if an update is ever interrupted.

## Habits that pay

- **Update between pieces of work, not during.** The Updates view
  will wait; a half-reviewed build shouldn't.
- **Engines move faster than Croo.** A weekly glance at the Updates
  view keeps the crew on current engines without making a hobby
  of it.
- **Unhurried, not postponed.** Nothing installs itself or interrupts
  your work, and there's never a countdown. But "between pieces of
  work" means today's gap, not someday — prompt is the habit; rushed
  is what Croo makes sure you never have to be.

Inside Croo? Just ask Nova.
