# Install Croo  (DRAFT 1, 2026-10-12)

*Croo Docs · 2026-10-12*

> DRAFT NOTE (never ships): aligned to consensus s261012105445 and the
> 2026-10-12 GO. This page describes the gated closed-beta journey —
> activation-required first run, manifest-driven download. It must not be
> published until that build actually ships; until then it would describe
> behaviour that is not live. No version numbers appear anywhere on this
> page by design — it never needs refreshing at a release cut.

Croo is installed by a coding agent, not by hand. You point an agent you
already trust at your installation link, and it does the careful parts —
fetching the right release, checking it, setting everything up — while
you stay in the loop for the few moments that are yours.

This page explains the whole journey. It can't install Croo by itself:
the download needs **your personal installation link**, which arrives in
your approval email.

## What you need

- The machine Croo will live on.
- A coding agent on that machine — the same kind of agent Croo itself
  runs. If you're in this beta, you almost certainly have one already.
- Your personal installation link, from your approval email.

## Your link, in one paragraph

The link is yours alone, and it is exactly one thing: **permission to
download the Croo beta**. It isn't your account password or your licence,
and holding it proves nothing about who you are — so don't post it
anywhere public, because anyone holding it can download. It keeps
working for as long as your invitation stands: a reinstall or a second
machine uses the same link, nothing is "used up". If it says your invitation
is not active, contact us. A temporary service or network failure is different:
your agent stops and explains the problem, and can try again later.

## Installing: one sentence from you

Tell your agent:

> Install Croo from <your installation link>.

That is genuinely the whole step. The link answers your agent with a
small machine-readable note that says what to do: where the full
installation instructions live, exactly which release is current, its
checksum, and a short-lived download address. You never type a version
number, a filename, or a checksum in this invitation flow. Your agent handles
those details; if it cannot verify the release, it stops and explains why.

**If you are an agent reading this page:** this page is the explanation,
not the instructions. Ask your person for their installation link; the
manifest it returns points you at the authoritative install document,
and its first field tells you how to proceed. While installing, verify
the archive's SHA-256 against the manifest **and** confirm the release
ID and hash against the public `version.json` on croolabs.com. Those two
must agree with each other and with what you downloaded — it's a
consistency check within Croo's own distribution, and on any
disagreement the right move is to stop and say so, never to guess at
another release.

## Installing is not activating

The link gets Croo onto the machine. Using Croo takes one more step,
inside Croo itself: a fresh install opens in **Activation required**,
and nothing wakes up until you activate.

- Enter your name and email and request your activation code.
- The code goes to the email your approval is on — this, not the link,
  is what ties the installation to you.
- Enter the code. Done.

Your 90-day beta starts at your **first successful activation** — not at
approval, not at download, not at install. Reinstalling, recovering, or
moving to another machine keeps your original dates; nothing resets by
reinstalling. If support has given you an activation key directly,
there's a place to enter that too.

Updates use Croo's enrolled private release channel, never your installation
link. Once that channel is configured, Croo shows available updates in its
Updates view. If it says the release channel is not configured, contact
support; the installation link is not an update credential.

## If something goes wrong

- **The link answers with a refusal.** Your invitation may have been
  suspended or withdrawn, or the link replaced. Write to
  support@croolabs.com from your approved email.
- **The download won't verify.** Your agent refused a mismatched
  checksum — that's it doing its job. Have it try once more a little
  later; if the refusal persists, send us the exact message.
- **Installed, but no activation code arrives.** Check that you're
  requesting with the approved email, and check spam. Still nothing —
  write to us.
- **You think the link leaked.** Tell us; we replace it. A replaced link
  means the old one stops working — that's the system working, not
  breaking.

Once you're activated, Nova takes it from here. The Operator's Manual
starts at the beginning — your first sit-down with your crew — and from
that point on, the answer to almost every question is the same: just ask
Nova.
