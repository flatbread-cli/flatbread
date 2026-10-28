# Commands

## Share your first run

1. Install it: `npm install -g flatbread-cli`. You need Node.js 20 or newer (nodejs.org).
2. Connect your agents, once: `flatbread setup`. Then you can share from their chat. Updates keep it current, and an agent you install later is connected the next time Flatbread runs, so you never run it again.
3. When a session is done, say `share this run` in its chat, or run `flatbread share` in a terminal. From a terminal it says which session it took. Not the session you meant? It prints the command for every other tool's newest, such as `flatbread share gemini`.
4. A review page opens in your browser. It runs on your own computer (`127.0.0.1`), and nothing has left it yet. No tab? Open the link the terminal or your agent printed.
5. Check it. Keys, passwords and personal details are already hidden. Hide more words if you like, and choose who can open the run: Private (only you), Unlisted (anyone with the link) or Public.
6. Press Confirm & share. Not signed in yet? Press Sign in to Flatbread first: it opens a new tab, and this page keeps what you chose.
7. Copy your link: the page that follows shows it, with Copy link.

## Every command

| Command                       | What it does |
| ----------------------------- | --- |
| `flatbread setup`             | Connect the agents on this computer, once |
| `flatbread share`             | Share your newest session, from whichever tool wrote it |
| `flatbread share <tool>`      | Share one tool's newest instead: claude, codex, gemini... |
| `flatbread pull <run>`        | Print a run's execution brief, for your agent to read (its ID or link) |
| `flatbread search <words>`    | Find shared runs: public ones, and your own when signed in |
| `flatbread login`             | Sign in. Share asks you to when it needs to |
| `flatbread whoami`            | Show who is signed in on this computer |
| `flatbread logout`            | Sign this computer out |
| `flatbread doctor`            | Something not working? Checks this computer and says what to do |
| `flatbread tools`             | The tools Flatbread reads, and what each one records |
| `flatbread setup --uninstall` | Undo setup |
| `flatbread mcp`               | What setup connects your agents to. They start it, not you |

`flatbread --help` prints every option, and `flatbread --version` the version.
`flatbread doctor --json` and `flatbread whoami --json` print one JSON object for an agent to read.
Exit code 0 means done (doctor: ready; whoami: signed in); 1 means not, with the reason on screen.
