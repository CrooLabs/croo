# Croo FAQ  (DRAFT 3.2, 2026-10-13)

*Croo Docs · 2026-10-13*

> DRAFT NOTE (never ships): base = the five questions live on the website's
> How page (CROO F.A.Q., captured 2026-10-13), kept in their site wording
> where it still holds; everything else is seeded from the docs set (manual,
> README, cli.md, support.md, reach.md, install.md) — short answer here, the
> owning doc holds the truth. The "Installing and activating" section shares
> install.md's hold: it describes the gated closed-beta journey and must not
> publish before that build ships. Three operator calls pending: the
> cost/beta wording (README's open call), whether the day-90 answer may name
> the Free fallback publicly, and the telemetry answer's exact wording.

## The basics

**What is Croo?**
Croo is where multi-agent work meets human control. Pick the engines, name
your Croo, and decide what goes ahead at every review.

**What's Nova?**
Nova is your first agent — the one Croo sets up with you at install. She
runs your crew day to day, answers your questions, and walks you through
anything on these pages you'd rather not do by hand. The Operator's Manual
starts with her.

**Which AI engines does Croo work with?**
Claude, Codex, AGY and Grok — your agents run on the engine subscriptions
you already have. Each engine is good at different things; chapter 8 of the
manual is the field guide.

**How many agents can I have?**
A crew, not a swarm: a core of long-lived agents that keep their names,
roles and memory, led by Nova. There's no practical limit baked into the
beta — in practice your engine subscriptions are the ceiling, because every
agent draws on one.

**Do I need to know the terminal?**
No. Croo's workspace is a browser page, and Nova does the technical parts.
There is a small set of terminal commands, but they're a recovery room, not
a second workspace — see the command-line guide (cli.md) for the handful
worth knowing.

**Does Croo work offline?**
Croo itself runs entirely on your machine — but your agents' engines are
cloud services, so real work needs an internet connection. Offline, the
workspace still opens; the crew just can't think.

**What does it cost?**
The closed beta runs on a complimentary 90-day term per person, starting at
your first activation. You pay your engine subscriptions as you already do;
Croo spends nothing on its own. [DRAFT: wording tracks the README's open
"free during the beta" call — align the two when the operator decides.]

## Getting in

**How do I join?**
The beta is invitation-only. Ask to join on the website; approval arrives by
email with your personal installation link.

**What happens when my 90 days end?**
Your term is 90 days from first activation, not from approval or install.
[DRAFT: agreed behaviour is that an admitted, expired user falls back to the
Free tier rather than losing access — PENDING the operator's call on saying
that publicly before launch pricing exists.]

## Where Croo should live

**Which machine should I install Croo on?**
One that stays on. Your crew works while you're away, answers on your
phone, and keeps its memory — none of that happens on a machine that's
asleep in a bag. The ideal is a spare Mac mini or a small Linux box in a
corner: install once, and reach it from anywhere (see reach.md). Croo runs
on macOS and Ubuntu.

**Can I just put it on my laptop?**
You can, and it's a fine way to try Croo. But close the lid and the crew
stops with it — agents mid-task pause, your phone goes quiet, and they pick
up again only when the laptop wakes. If you find yourself wanting Croo
*there* while you're *here*, that's the moment for an always-on machine.
Moving later is easy (see "Can I move Croo to another machine?").

**Does it need to be a powerful machine?**
No. Croo itself is light — the thinking happens on your agents' engines,
not on the box. A modest machine that stays on beats a fast one that
sleeps. What matters more: plenty of disk for your projects, and a reliable
connection.

**I'm on Windows.**
Croo runs on Ubuntu, so a Windows 11 PC with a dedicated Ubuntu install
works — Nova handles the install the same way. Ubuntu under WSL2 should
work too, but we haven't tested it yet; ask us before relying on it.

**Anything to set on the machine itself?**
Only that it doesn't sleep. Ask Nova at install — "make sure this machine
stays awake" — and she'll check the energy settings with you.

## Installing and activating

**How do I install Croo?**
Tell a coding agent you already trust: "Install Croo from <your installation
link>." The agent fetches, verifies, and sets up the right release — you
never type a version number or checksum. The install page covers the whole
journey, including the few moments that are yours.

**Can I reuse my installation link?**
Yes — a reinstall or a second machine uses the same link, for as long as
your invitation stands. It's permission to download, nothing more; don't
post it anywhere public.

**Is the link my licence?**
No. Installing and activating are separate: the link gets Croo onto the
machine, and a fresh install opens in Activation required. You activate
inside Croo with a code sent to your approved email — that code, not the
link, is what ties the installation to you. Your 90 days start at first
successful activation, and reinstalling never resets them.

**Can I move Croo to another machine?**
Yes. Your installation link installs there too, and activating with your
approved email carries your licence over — your original dates are
preserved, nothing resets. Nova can write a handoff of your crew's state
before you move.

**Do I need accounts with the engines?**
Yes — agents run on the engines you already have. Croo orchestrates them;
it doesn't resell them. The usage view (chapter 8) shows what each agent is
drawing from which subscription.

## Working with your crew

**Can I step in when an agent gets it wrong?**
Stop or redirect an agent at any time. One red button cuts off every
standing approval at once.

**What's a standing approval?**
Permission that outlives one question — "yes, and don't ask again for this
kind of thing." It saves you twenty routine yeses in a row; the red button
revokes them all at once and everyone asks again. Chapter 7.

**Can my agents check each other's work?**
Yes. Hand one agent's output to another for review, or put them in a
discussion and read the exchange. Everything they pass each other goes
through mailboxes you can inspect.

**Can I bring an agent I already have?**
Yes. There's a careful hand-over procedure — config first, a structured
handoff, then verification before the old session retires — and Nova walks
you through it. Don't improvise this one; ask her.

**Can I talk to Croo — actual voice?**
Both ways. On your phone, tap the microphone and speak, and hear replies
read back; driving mode goes fully hands-free. Chapters 4 and 9.

**What's the Playground?**
For the kids ;) — a few small games shipped with Croo, for while an agent
works. Your own additions appear in the menu too. Chapter 10.

## Privacy

**Where does my code go? Is it private?**
Prompts go only to the engine you chose for that agent. Everything Croo
keeps (logs, settings, your agents' files) stays in one folder on your
machine.

**Does Croo send telemetry?**
No app-added telemetry. Croo's own outward traffic is what you'd expect:
your agents talking to their engines, and an update check that fetches a
file. [DRAFT: exact wording pending the operator's clearance.]

**What happens to my data if I uninstall?**
It stays yours and stays put. Everything Croo keeps lives in that one
folder, and your projects were always your own files — removing Croo
doesn't take them with it.

## Away from the desk

**Can I use Croo from my phone?**
Two honest ways. Telegram needs no network setup at all and puts your crew
in your pocket — Nova sets it up with you. For the full workspace on
another device, Croo supports Tailscale, a private network between your own
devices. Both are in reach.md.

**Is Tailscale required?**
No. It's only for opening the full workspace from another device. Telegram
needs nothing opened up at all, and at the desk Croo is complete as it is.

**Can my crew keep working while I'm away?**
Yes — agents carry on with what's in front of them, queue what needs you,
and your cues can reach your phone when something genuinely shouldn't wait.
Chapter 9.

**Is Croo exposed to the internet?**
No. The workspace is served on your machine only (`127.0.0.1` — this
computer, no other); nothing about Croo listens to the internet. Reaching
it from your other devices uses your own private network — see reach.md.

## Keeping Croo current

**How do updates work?**
Croo checks, explains, and offers — it never installs an update on its own.
When the Updates view shows something, plan to apply it at the next natural
pause; current is the healthy state. Chapter 11 of the manual has the why.

## When something's off

**My computer rebooted. Did I lose my crew?**
No. After a reboot, `croo respawn` brings every registered agent back, each
resuming its own conversation — or just ask Nova once the workspace is up.
The order that works is in chapter 12 and cli.md.

**The workspace won't load. Is everything lost?**
Almost certainly not — the workspace being down doesn't take Nova with it.
`croo attach nova` in a terminal puts you in front of her directly; from
there she can usually fix the rest. The ladder is in chapter 12 of the
manual and in cli.md.

**How do I report a problem?**
Easiest: ask Nova — "write up a report of what just happened, for Croo
support" — and send it to support@croolabs.com. The by-hand checklist is in
support.md.

**What's safe to include in a support report?**
Never passwords, tokens or key files — we delete those on sight. Send
excerpts, not whole transcripts; the exact error beats a description of it.
support.md has the full rules.

**Something else?**
On the website, ask Nina — the chat in the corner; she answers from what
we've published. Inside Croo, ask Nova. Otherwise: support@croolabs.com.
