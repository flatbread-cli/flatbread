# Changelog

The versions of `flatbread-cli` on npm.

## 0.9.7 - 2026-10-27

- `flatbread guard` is removed. It reached 0.9.6 as an unannounced preview of a Teams feature that
  is not built yet.

## 0.9.6 - 2026-10-27

- A key with no known prefix is hidden too: 32 or more random-looking characters (an AWS secret
  access key, a signing secret in `.env`) become `«REDACTED:high_entropy»`. A git commit hash, a
  UUID, a file path and a lockfile's `sha512-` hash are left alone.
- The brief an agent pulls says what the run did, in order: one line per command, read, edit and test
  run, with each failure's first line. It lists the files the agent read, and an edit made through the
  shell (`python3 - <<'E' ...`, `sed -i`, `cat > file`) is quoted as it ran, because no diff exists for
  it. A test run after such an edit now counts as a test after the last edit.
- Sharing without code now also hides the code inside a shell command that wrote a file.
- The agent's search tool refuses an argument it does not take, rather than searching without it.
- The review page is easier to read: a long output or input is folded behind + with its line count and
  how many redactions it holds (a failure is never folded), and the sidebar's jump opens it; no times
  on the cards; a tool from an MCP server is named by its tool; the agent's bold and code read as such;
  each redaction says where it is in words (`output`, `command`) rather than as a field path.
- Code is no longer hidden as a secret. A line like `const token = request.cookies.get(NAME)?.value`,
  `secret = process.env.SESSION_SECRET` or `verify(token: string)` names where a secret comes from
  and holds none, so it is shared as written. A value with a quote in it, or any plain value such as
  `password=hunter2`, is still hidden.

## 0.9.5 - 2026-10-26

- `flatbread setup` is a one-time step. After an update, or when you install another agent, the next
  run of Flatbread (yours, or an agent starting its server) brings setup up to date by itself, with
  nothing printed. It connects all eight agents, so each can share from its chat, and prints one line
  per agent.
- Flatbread finds sessions itself: `flatbread share` takes your newest, `flatbread share gemini` one
  tool's newest. The commands are `share`, `setup`, `pull`, `search`, `login`, `logout`, `whoami`,
  `doctor`, `tools` and `mcp`; `flatbread pull <run> > brief.md` saves a brief, and `search --tool`
  narrows a search to one tool.
- One name for what a run teaches the next agent: the execution brief, which the MCP tool
  `flatbread_get_brief` returns.
- Every tool's runs carry the same facts. A number a tool does not record (token usage, files changed,
  failures) reads "not recorded", with which tool and why, never 0 or a blank; `flatbread tools`
  lists what each records. Codex's file edits and Copilot's `edit` calls show their diffs, and every
  Codex session counts the files its patches changed.
- Less to read: `flatbread share` prints the title, how many prompts and tool calls, what it hid, where
  to press Confirm, then who can open it and the link. `login`, `logout`, `whoami` and `doctor` say
  one plain line each; paths and rule ids are behind `--details`.
- Tools are named the way people write them: `gemini`, `gemini-cli` and "Gemini CLI" are the same.
  A mistyped command gets the one it nearly was ("Did you mean flatbread share?").
- On Linux, when the agent started Flatbread without the display variables, the browser tab is
  opened with the display of the program that started it. A missing browser launcher no longer
  stops the MCP server.

## 0.9.4 - 2026-10-25

- `flatbread share` and `flatbread parse` with nothing after them take the newest session on this
  machine, whichever agent wrote it, and say which: "Sharing your newest OpenCode session (written
  2 min ago)", then the command for each other agent's newest. Before, they always took Claude Code's.
- Name the agent or the file with no flag: `flatbread share opencode`, `flatbread parse codex`,
  `flatbread share ./session.jsonl`. `--file`, `--harness` and `--latest` still work.
- `flatbread parse` ends on the command that shares what it just read, to copy and paste.
- Codex starts its MCP servers with only a few environment variables (no `DISPLAY`), so "share this
  run" in Codex could not launch a browser tab. `flatbread setup` now passes the display variables
  through. Run `flatbread setup` again after updating, then restart Codex.
- The agent hands you the review link every time, and never says a tab is open, because it cannot
  know. Asking again closes the earlier review (unshared) and opens a fresh one with every prompt so far.
- An old review tab can no longer confirm or cancel a newer review: each review page carries its own
  id. Reloading a finished review shows "This review has ended" instead of "Confirm Form Resubmission".
- A word you add to redact is not looked for in the run's title; the built-in secret rules still are.
- A Claude Code log line of a kind this version does not read is said plainly, with the update command.

## 0.9.3 - 2026-10-25

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

## 0.9.2 - 2026-10-25

- Sharing from Codex leaves the share request out again. Codex 0.164 calls `flatbread_share` from a
  script, and its reading of the flatbread skill and its look at its tool list were kept as the
  turn's work, so "share this run" and the skill file were shared with the run. Reading the flatbread
  skill on the way to a share is not work in any harness.
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
