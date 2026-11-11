# Start a CLI agent through Herdr

Read this file when Herdr is already installed and this Grok Bot is about to start or supervise a local interactive CLI agent. This is the normal path.

Use the `herdr` binary and session verified on this machine. Official behavior, supported kinds and exact flags come from the installed binary and [Herdr's current documentation](https://herdr.dev/tui/), especially [Agent automation](https://herdr.dev/tui/docs/agent-automation/). Prefer `herdr --help` over any copied example.

1. Inspect live workspaces, panes and agents with documented native commands such as `herdr status`, `herdr workspace list`, `herdr pane list` and `herdr agent list`. Prefer the project's existing workspace when appropriate. Use IDs returned by Herdr, not the current UI focus or guessed pane numbers.

2. Start a uniquely named worker only in an available foreground shell pane, with the requested `--kind` and documented native arguments, for example `herdr agent start NAME --kind KIND --pane PANE_ID`. Names must be unique and should make the bot or task easy to recognize. Do not restart the shared Herdr service, create an unnecessary server, change unrelated configuration, or take over a busy pane or worker. Preserve the user's focus during background work. Keep the agent visible in Herdr so the user can monitor status and intervene.

3. Confirm the agent is ready, with no unresolved sign-in, trust or approval dialogue. Submit the prompt once with `herdr agent prompt`, passing the complete prompt as one safely quoted data argument. Do not use `eval`, fabricate Herdr caller environment variables, weaken sandbox, approval or hook-trust controls, or submit work to a busy or blocked agent.

4. Read the actual reply with native commands such as `herdr agent get` and `herdr agent read`. Inspect files or other outputs when the task produces them. A submission acknowledgement, exit code 0, `idle` or `done` is not by itself a correct result. If the agent is blocked, stalled, timed out or uncertain, inspect the existing worker and report its verified status, pane and actual result or blocker. Do not blindly retry an uncertain submission, restart an agent, or replay a historical uncertain task. Keep active workers available for user inspection and intervention.

The external Grok Bot may report only facts it has verified, such as worker, pane, workspace and working directory. Do not ask the CLI worker to rediscover or print environment variables merely to prove it is inside Herdr.

If this Grok Bot hands the work to another bot that will start or supervise a CLI agent, include the complete Herdr setup facts for this machine, this skill, the project, the requested task, the output location and who should receive the report. A bare "follow the previous instructions" is not enough.

If the installed binary does not support the requested agent kind, stop and tell the user. Never guess a launcher, wrapper or unofficial command path. Never spoof `HERDR_ENV`.
