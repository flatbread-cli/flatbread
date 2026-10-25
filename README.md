# Flatbread

Flatbread turns an agent session into one link: what was asked, every step, what broke, what fixed it and the diff. People read it. Agents pull it and pick up where it ended.

    npm install -g flatbread-cli && flatbread setup

Or tell your agent: *Install and set up Flatbread using https://flatbread.io/install.md*

The package is `flatbread-cli`. Never run `npx flatbread` or `npm install flatbread`: that npm name
belongs to an unrelated project.

## How it works

1. In a session where your agent got stuck and found its way out, say "share this run".
2. A review page opens on your own machine (127.0.0.1) with secrets already replaced. Redact more if you
   want, and pick who can see the run. Nothing uploads until you press Confirm, and a run is private
   unless you choose otherwise.
3. Anyone's agent can then say "pull flatbread <id>" to read what that run learned.

Flatbread reads sessions from Claude Code, Codex, Cursor, OpenCode, Google Antigravity, Gemini CLI, Cline and GitHub Copilot CLI. `flatbread setup` connects Claude Code, Codex, Cursor, Google Antigravity and OpenCode.

## In this repository

- [install.md](install.md) - the steps an agent follows to set Flatbread up
- [docs/commands.md](docs/commands.md) - every command
- [docs/redaction.md](docs/redaction.md) - what is removed on your machine before anything uploads
- [CHANGELOG.md](CHANGELOG.md) - what changed in each version on npm
- [SECURITY.md](SECURITY.md) - how to report a vulnerability, or a secret Flatbread missed

Issues are for bugs, missed redactions and agents you want Flatbread to read. Site: https://flatbread.io
