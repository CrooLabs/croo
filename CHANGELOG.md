# Croo Changelog

Release notes for activated Croo releases, newest first.

## v1.0.03 - 15 October 2026

<!-- release_id: croo-1003-R1 -->

### Project Git

- Set project-wide Git guidance for a shared branch or separate agent workspaces,
  with clearer setup instructions and branch suggestions.
- Follow branches, commits and file changes in a visual Git activity view,
  with recorded agent contributions and readable commit descriptions.
- Ask Nova to guide you through a Git example, and copy agent instructions
  directly from project settings.

### Files and Interface

- Open PDFs, images and supported media inside Croo, then close the viewer to
  return to your work. View and copy the file path without leaving the preview.
- Read larger pinned-draft previews, identify attachments by their paperclip,
  and use an improved message-box layout in narrow panels.
- See active, waiting and Power-through-enabled agents in the refreshed fleet
  summary. Sidebar file names are easier to read.

### Engine Controls

- Compact AGY conversations directly from Croo on supported engine versions.
- Get clearer confirmation when changing a Codex model or reasoning effort,
  with fixes for numbered question choices and approval buttons.
- Find relevant commands in refreshed engine-specific More menus, with
  improved Grok approval handling and cleaner conversation output.

## v0.9.78 - 11 October 2026

<!-- release_id: croo-978-R1 -->

**The agent header shows the model an agent is really running, new files
appear in the sidebar search without a reload, and the chat view stays clean.**

- The agent header no longer falls back to an account default while a message
  is queued behind an Antigravity turn.
- A file an agent writes after the page opened appears in the sidebar search
  within a minute, or as soon as you click into the search box. The file list
  also loads much faster.
- Codex's "send input to terminal N?" approval is answered by Power Through
  and by the choice buttons.
- The chat view hides Claude's idle-compaction bookkeeping instead of showing
  it as a reply.
- Voice setup help says which part is missing.
- The project header's map and settings buttons sit flush right.
