# Reach Croo from anywhere  (DRAFT 2, 2026-10-12)

*Croo Docs · 2026-10-12*

Out of the box, Croo's workspace is served **on your machine only** —
the address is `http://127.0.0.1:9875`, and 127.0.0.1 always means
"this computer, and no other". That's a deliberate security posture,
not a limitation to fix: nothing about Croo listens to the internet.

This page is about the two honest ways to reach your crew when you're
not sitting at that machine.

## The zero-setup way: Telegram

If what you want is your crew on your phone, you may not need any of
this. **Telegram needs no network setup at all** — Croo reaches
outward to Telegram, so it works from anywhere your phone has signal,
with nothing opened up on your machine. Nova installs it with you;
chapter 9 of the manual covers what it can do (bind to an agent,
one-tap answers, voice in and out, your cues when you're away).

Set that up first. Come back here if you also want the full phone
interface — the picker, the chat view, driving mode — or the whole
workspace on another device.

## The full way: a private network between your own devices

To open the workspace from your phone, tablet or another computer,
that device needs a private path to your Croo machine. The way Croo
supports is **Tailscale**: a free-for-personal-use service that
connects your own devices into a small private network. Only devices
signed in to *your* Tailscale account can reach each other — it is
not "putting Croo on the internet", it's carrying your living room
with you.

The setup, start to finish — and the honest recommendation first:
**don't do this by hand, ask Nova.**

> "Nova, set up Tailscale so I can reach Croo from my phone."

She runs what can be run for you, hands you the rest ready to paste,
and checks each step worked. The list below is so you know what she's
doing and why. Two moments are always yours: anything that asks for
your computer's password, and signing in — Nova never needs your
passwords or your Tailscale login.

1. **Create a Tailscale account** — free for personal use, at
   tailscale.com.
2. **Nova installs Tailscale on the Croo machine and connects it.**
   When she runs the connect step, Tailscale prints a **login link**
   — you click it, sign in in your browser, and the machine joins
   your private network. Nothing secret is typed into the chat.
   *(Prefer fully hands-off? Generate a **one-time, short-expiry
   auth key** in your Tailscale admin console and hand it to Nova in
   the moment — she joins the machine with it directly. Treat the
   key like a house key: single use, expires on its own, revoke it
   in the console once the machine is connected.)*
3. **Put Tailscale on your phone** (or other device) yourself — the
   app from the store, signed in to the same account. This half is
   always yours; Nova can't do your phone.
4. **Switch on Tailscale Serve for the workspace.** Croo itself never
   listens beyond 127.0.0.1 — Serve relays the workspace to your own
   devices, tailnet-only. One command; it asks for your computer's
   password, so you type it, with Nova handing it to you ready to
   paste.
5. **Save the address.** Once Serve is on, `croo access` prints your
   machine's `https://…ts.net` address beside the local one, labelled
   "from other devices on your tailnet" — open that from your phone
   and add it to your home screen. Chapter 9's phone interface takes
   over from there.

## What never to do

- **Never port-forward Croo on your router,** and never serve it on a
  public address. That includes Tailscale's own "Funnel" feature,
  which makes things public — Serve yes, Funnel never. Croo's
  workspace is built for private paths; the internet is not one.
- **Treat the Tailscale account like a key to your house** — any
  device signed in to it can reach your workspace. Don't share the
  account, and remove devices you no longer use.

Inside Croo? Just ask Nova.
