# Changelog

The versions of `flatbread-cli` on npm.

## 0.9.2 - not yet published

- A shared run ends before the prompt that asked for the share, in every harness: the prompt, the
  `flatbread_share` call and whatever the agent did on the way there (reading the skill, listing its
  tools) are left out. Codex 0.164 calls `flatbread_share` from a script, and that script is the
  share call too. A prompt that says "fix it, then share it" is left out whole.
- A skill's text is never part of a run, whichever skill it is and whichever harness ran it. The
  call that loaded it stays (which skill, which file); its text becomes `«REDACTED:skill_content»`:
  Claude Code's `Skill`, OpenCode's `skill`, Cline's `skills`, Gemini CLI's `activate_skill`, any
  read of a `SKILL.md` or of a file in a skills folder under a dot-folder (`~/.claude/skills/`,
  `~/.agents/skills/`, `.github/skills/`), and any result that opens like a skill. A prompt the
  harness wrote that is a skill is dropped. A failed read and a write to a skill's file stay.
- No more "Human intervention". A prompt that arrives while a tool is failing does not say whether
  the person was fixing it, so the failure is unresolved: "Still failing at the next prompt".
- Codex: a skill named in the chat (`$flatbread`), whose whole SKILL.md Codex adds as a user message,
  is not a prompt, nor is an integration's `<external_...>` context. A shell command you ran with `!`
  reads as `! cmd`.
- The review page's sign-in line names the code as its own (`Your code is ...`), the one the
  approval tab should show.

## 0.9.1 - 2026-10-24

- Claude Code: a prompt is what a person typed. A loaded skill's text, a subagent's report, a task
  notification, a slash command's output, the interruption marker and the other lines Claude Code
  writes itself are no longer prompts, so "from prompt N" and its earlier-prompts count match the
  chat. A slash command reads as typed (`/review PR 12`), and `parse` names what it set aside.
- Claude Code: a background subagent's card shows its report and its counts, not "Async agent
  launched".
- The review page has no keyboard triage. Its Sign in opens an approval page that names the review
  page, not a terminal.
- Antigravity: a tool argument that is a JSON string JSON refuses is still decoded, and
  `adapters --describe antigravity` says how many `.db` conversations also have a transcript.

## 0.9.0 - 2026-10-24

- `flatbread setup` registers OpenCode's MCP server in `opencode.json`, and never rewrites a JSONC file.
- `adapters --describe antigravity` lists every `~/.gemini/antigravity*` folder with its counts.

- `flatbread doctor`: checks Node 20+, that the CLI is not running from npx's cache, that setup is
  current, and who is signed in, then prints the one next step. Exit 0 when ready.
- `--json` on `flatbread doctor` and `flatbread whoami`, for an agent to read.
- `flatbread --version`.
- `--help` lists the exit codes.

## 0.8.0 - 2026-10-23

- Reads Gemini CLI, Cline and GitHub Copilot CLI sessions.
- `flatbread share --to`: share only up to a prompt, by its number or words from it.
- `flatbread share --redact <word>`, and words added on the review page. This machine's username is
  redacted wherever it appears as a word, including in paths written with hyphens.
- Confirm always shares to your account; signed out, the review page signs you in.
- A subagent's work shows as one card.
- `flatbread capture` is gone. `flatbread setup` registers the MCP server and the skill, nothing else.

## 0.7.0 - 2026-10-19

0.6.0 was never published; its changes are in this version.

- Say "share this run" in the chat: the `flatbread_share` MCP tool finds the session and opens the
  review page. Confirm is still the only way anything uploads.
- The Codex reader was rebuilt from real sessions: exit codes, MCP call status and changed files.
- Search offers the closest runs, labelled as closest, when no run has every word.

## 0.5.0 - 2026-10-19

- `flatbread setup` registers the MCP server for Codex, Cursor and Google Antigravity, and writes the
  skill for Antigravity and OpenCode, each only where installed.
- `flatbread search --recovered` was removed.

## 0.4.0 - 2026-10-19

- Reads Codex CLI sessions.
- `flatbread setup` writes a skill that tells the agent when to search Flatbread, for Claude Code and
  `~/.agents/skills`.

## 0.3.2 - 2026-10-19

- An agent that never records how a tool call ended no longer shows a failure count.

## 0.3.1 - 2026-10-19

- `flatbread setup` registers the MCP server.
- Reads Google Antigravity sessions.
- The review page was restyled.

## 0.3.0 - 2026-10-19

Published without release notes.

## 0.2.0 - 2026-10-18

- Run briefs and Context Capsules; `flatbread search`, `flatbread setup` and `flatbread capture`.

## 0.1.0 - 2026-10-18

First release on npm.
