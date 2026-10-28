# Flatbread

Flatbread turns an agent session into one link: what was asked, every step, what broke, what fixed it and the diff. People read it. Agents pull it and pick up where it ended.

The package is `flatbread-cli`. Never run `npx flatbread` or `npm install flatbread`: that npm name
belongs to an unrelated project.

## Share your first run

1. Install it: `npm install -g flatbread-cli`. You need Node.js 20 or newer (nodejs.org).
2. Connect your agents, once: `flatbread setup`. Then you can share from their chat. Updates keep it current, and an agent you install later is connected the next time Flatbread runs, so you never run it again.
3. When a session is done, say `share this run` in its chat, or run `flatbread share` in a terminal. From a terminal it says which session it took. Not the session you meant? It prints the command for every other tool's newest, such as `flatbread share gemini`.
4. A review page opens in your browser. It runs on your own computer (`127.0.0.1`), and nothing has left it yet. No tab? Open the link the terminal or your agent printed.
5. Check it. Keys, passwords and personal details are already hidden. Hide more words if you like, and choose who can open the run: Private (only you), Unlisted (anyone with the link) or Public.
6. Press Confirm & share. Not signed in yet? Press Sign in to Flatbread first: it opens a new tab, and this page keeps what you chose.
7. Copy your link: the page that follows shows it, with Copy link.

Rather have your agent do steps 1 and 2? Tell it: *Install and set up Flatbread using https://flatbread.io/install.md*

Anyone's agent can then say "pull flatbread <id>" to read what that run learned.

Flatbread reads sessions from Claude Code, Codex, Cursor, OpenCode, Google Antigravity, Gemini CLI, Cline and GitHub Copilot CLI. `flatbread setup` connects Claude Code, Codex, Cursor, Google Antigravity, OpenCode, Gemini CLI, GitHub Copilot CLI and Cline.

## In this repository

The docs, the changelog and the issue forms. The CLI is published on npm as `flatbread-cli`; its source is not
published here.

- [install.md](install.md) - the steps an agent follows to set Flatbread up
- [docs/commands.md](docs/commands.md) - every command
- [docs/redaction.md](docs/redaction.md) - what is removed on your machine before anything uploads
- [CHANGELOG.md](CHANGELOG.md) - what changed in each version on npm
- [SECURITY.md](SECURITY.md) - how to report a vulnerability, or a secret Flatbread missed

Issues are for bugs, missed redactions and agents you want Flatbread to read. Site: https://flatbread.io
