# README-FOR-ADAM — how this repository is shaped and fed

*Internal. The one file here that never ships: delete it the day the repo
goes public.*

## The shape

```
README.md          front page — what Croo is, the join link, the standing line
LICENSE.md         commercial notice; one carve-out for playground/
manual/            the Operator's Manual: 00 table of contents + chapters 01–12 (.md),
                   plus the PDF edition alongside when you've made it
docs/              install, cli, reach, support, faq — markdown, stays markdown
playbooks/         one short page per field (.md + PDF alongside): Software done, Startup/Law coming
playground/        MIT-licensed: the shipped games as HTML + the authoring guide, added from each release
examples/ tips/ screenshots/   placeholders until filled
```

Nothing in this repository is product source, and nothing ever will be.

## The rules

- **We own the markdown.** Every page here is derived from Silver's locked
  source, posted to Slack #croo-docs-source. Edits go there, never here:
  send a re-derive note and the page comes back re-locked.
- **PDFs are derived.** The manual and each playbook get a PDF edition —
  same text, same version stamp (`Croo Operator's Manual · v1.0 ·
  2026-10-12` and so on) — made by you from the posted markdown and
  returned via #croo-docs-source. We place them here, beside the .md.
- **Markdown stays beside the PDF.** GitHub renders .md in the browser and
  every "see chapter 7" link points at a chapter file; the PDF is for
  front-to-back reading and printing.
- **No version numbers in docs pages.** The install page is deliberately
  static; release facts live at croolabs.com/croo/version.json.
- **Private until launch day.** Visibility flips to public then, by the
  operator. Before that flip: delete this file, and remove every
  `> DRAFT NOTE (never ships)` block.

## What's held, and why

- `docs/install.md` and the "Installing and activating" section of
  `docs/faq.md` describe the gated closed-beta journey (personal
  installation link, activation-required first run). They must not be
  public before that build ships — their draft notes say so.
- `docs/faq.md` carries three bracketed `[DRAFT: …]` markers awaiting the
  operator's calls (cost wording, day-90 answer, telemetry wording).
- `README.md` has one HTML comment marking the join URL to confirm.
- `playbooks/software.md` is draft 3, not yet read by the operator.
- `LICENSE.md` is a draft pending legal review.
- `playground/` has its README and licence; the game folders and the
  authoring guide are extracted from a release by Sally, after her
  third-party-code and portability checks.
- A `CHANGELOG.md` (release notes, generated from croolabs.com/croo/changes/)
  is designed and parked; it lands when the activation step writes those files.

*Silver · 2026-10-13*
