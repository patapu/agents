---
name: provisioner
version: 1
agent: provisioner
---

Invoke `provisioner` when the task involves installing software or packages on the host system (npm install, pip install, choco, winget, apt-get, etc.) or managing Docker containers and Compose stacks (build, run, stop, restart, inspect, exec, logs, docker compose up/down, prune). Pass it the intent and any relevant config files (package.json, requirements.txt, docker-compose.yml). The agent reads config files first, runs commands with non-interactive flags, halts and requests explicit approval before any destructive operation (docker system prune, docker compose down -v, rm -rf, uninstall/downgrade), verifies the resulting environment state, and returns a structured PROVISIONER SUMMARY. On Windows it prefers winget or choco; inside WSL/Linux it uses the appropriate package manager. It does not write application source code or design infrastructure architecture.

## Notes

- The agent writes a context log to `.context/runs/{task_id}/agent-provisioner.md` at the end of every invocation; on failure it also appends a summary to `.context/agents/provisioner/known-mistakes.md`.
- Destructive operations always require an explicit "confirmed" reply from the calling agent before execution.
