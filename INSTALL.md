# Install Herdr and official skills

Read this file only when `herdr` is missing or not usable on the computer this Grok Bot will use to launch local CLI agents. Ask the user before running an installer or installing skills.

This is a setup guide for people who use [Grok Bot](https://grok.com). It is not official Herdr documentation, and it is not a Herdr or xAI product. If these commands ever differ from Herdr's current docs, follow the official pages.

## 1. Install Herdr

Official page: [Install Herdr](https://herdr.dev/tui/docs/install/).

On Linux or macOS:

```bash
curl -fsSL https://herdr.dev/install.sh | sh
```

On Windows, use the official PowerShell installer:

```powershell
powershell -ExecutionPolicy Bypass -c "irm https://herdr.dev/install.ps1 | iex"
```

If endpoint security blocks that command, the same page has a Command Prompt installer. If the user already uses Homebrew, the official option is `brew install herdr`. Official docs also list mise and Nix; use those only when the user already works that way.

After install, if the shell cannot find `herdr`, restart the terminal or confirm the install directory is on `PATH`. Verify with `herdr --version`.

Then, from a project directory, start Herdr the usual way:

```bash
herdr
```

This uses the default background session. Do not invent a custom socket layout, do not create an extra server just to run one task, and do not copy paths from another computer. If the user already has a named session they want to keep, honor that session; otherwise stay on the default.

Remember only facts verified on this machine, such as a binary path that is not on `PATH`, or a session name the user already chose. Keep those in this user's memory or a local note they approved, not in the shared skill text.

## 2. Install Herdr's official skills

The official Herdr skill is for coding agents already running inside a Herdr pane. It lets those agents inspect neighboring work, start helpers, and coordinate with each other. Install it now so it is ready later. Official page: [Agent skill file](https://herdr.dev/tui/docs/agent-skill/).

The official installer is:

```bash
npx skills add herdrdev/herdr --skill herdr -g
```

The `-g` flag installs it globally for supported agents. Omit `-g` to install it only in the current project. Get the user's go-ahead first.

If Herdr is already installed, `herdr --skill` prints the copy bundled with that binary. For a manual fallback, use the repository copy linked from the official page, and install it as a skill named `herdr` in agents that have a skill system.

After this, start coding agents inside Herdr so they receive a real `HERDR_ENV=1`. The external Grok Bot follows this repository's `herdr-grok-bot` skill and must not spoof `HERDR_ENV` or caller pane context.

Useful official docs:

- [Herdr TUI](https://herdr.dev/tui/)
- [Quick start](https://herdr.dev/tui/docs/quick-start/)
- [Agent automation](https://herdr.dev/tui/docs/agent-automation/)
- [Agent skill](https://herdr.dev/tui/docs/agent-skill/)
