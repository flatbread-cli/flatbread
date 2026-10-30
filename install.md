# Install Flatbread

You are an agent setting up Flatbread for the person you work with. Run each step, read its
output, and stop to tell them if a step fails.

Flatbread turns an agent session into one link: what was asked, every step, what broke, what fixed it and the diff. People read it. Agents pull it and pick up where it ended.

## 1. Check Node.js

    node --version

It must be 20 or newer. If it is older or missing, stop and ask them to install Node.js 20+.

## 2. Install the CLI

    npm install -g flatbread-cli

The package is `flatbread-cli`. Never run `npx flatbread` or `npm install flatbread`: the npm name
`flatbread` belongs to an unrelated project, and it would run a stranger's code.

## 3. Connect the agents on this machine

    flatbread setup

This registers the Flatbread MCP server, and a skill that says when to use it, with Claude Code, Codex, Cursor, Google Antigravity, OpenCode, Gemini CLI, GitHub Copilot CLI and Cline - each
only where it is installed. It writes nothing else, and updates keep it current: setup is a one-time step.
`flatbread setup --uninstall` removes exactly what it added.

## 4. Check

    flatbread doctor --json

`ready` is true when this machine can use Flatbread, and `next` is the one thing to do next. The exit
code is 0 when ready and 1 when not.

## 5. Sign in (optional, a person has to do this part)

    flatbread login

It prints a page on https://flatbread.io and a short code, then waits. Give the person the page link and the code:
they open it, sign in, and check the code matches. You cannot approve it for them. Signed out, search
still reads public runs, and a share asks them to sign in on its review page.
`flatbread whoami --json` says who is signed in.

## 6. Tell them it is ready

Setup only takes effect in a new session: the agent has to restart (or the editor window reload) to start
the MCP server. Then they can say:

- "share this run" - opens a review page on their own machine (127.0.0.1). Secrets are already
  redacted there; they can redact more and pick who sees the run. Nothing uploads until Confirm is
  pressed there - that press is the user's, never yours - and a run is private unless they choose
  otherwise.
- "share this run from the prompt about X" - the same, for part of a long session.
- "pull flatbread <id>" - reads that run's execution brief (what was asked, where it failed, what fixed it)
  so you can apply it here. From a terminal: `flatbread pull <id>`.

Before a task, you can search Flatbread for runs where an agent already worked through the same problem.

From a terminal they can also run `flatbread share`. Flatbread reads sessions from Claude Code, Codex, Cursor, OpenCode, Google Antigravity, Gemini CLI, Cline and GitHub Copilot CLI.

Full docs: https://flatbread.io/docs
