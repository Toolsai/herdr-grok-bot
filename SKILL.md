---
name: herdr-grok-bot
description: >-
  Use when a Grok Bot is about to start a new local interactive CLI agent
  (for example Codex, Cursor, Antigravity, Claude Code, Pi, or another kind
  Herdr supports), even if Herdr is not mentioned; also when helping the
  user install Herdr or add this skill. Launch those agents through Herdr
  so the user can see each agent's status, workspace and conversation and
  intervene when needed. Do not use for ordinary short Shell commands,
  repository work that Grok Bot already routes through a cloud coding
  agent, or discussion-only tasks.
---

This is a lightweight Grok Bot convention, not Herdr's official skill and not a Herdr or xAI product. When starting a local interactive CLI agent, go through [Herdr](https://herdr.dev) so the user can watch each agent and step in. Ordinary short Shell commands and Grok Bot cloud coding-agent work keep their existing paths.

Helper files live beside this skill. Read only the file the current case needs. If you have already read that file, or already know this machine's Herdr setup, do not reread it; just run the documented native command, for example `herdr agent start unique-name --kind cursor --pane PANE_ID`, then `herdr agent prompt` and `herdr agent read`. Use a pane ID returned by Herdr, and a `--kind` the installed binary supports, such as `codex`, `cursor`, `agy`, `claude` or `pi`.

1. Check whether `herdr` is installed and usable (`herdr --version` or `herdr status`). If it is not, follow [INSTALL.md](INSTALL.md): install Herdr from the official docs, then install Herdr's official skills for coding agents.
2. If Herdr is already installed, follow [USAGE.md](USAGE.md) to start and supervise the CLI agent with native Herdr commands. That is the normal path. Stop there when the work is done.
3. If the user wants CLI agents to communicate or chain work through Herdr, do not invent a protocol. Point those in-pane agents to Herdr's official skill, already installed by [INSTALL.md](INSTALL.md), and to the official [Agent skill](https://herdr.dev/tui/docs/agent-skill/) docs. Print the copy that matches this install with `herdr --skill`.

Do not add other special cases. Never spoof `HERDR_ENV`.
