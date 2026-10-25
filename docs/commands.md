# Commands

| Command                                 | What it does |
| --------------------------------------- | --- |
| `flatbread login`                       | Sign in through the website |
| `flatbread logout`                      | Delete the stored credentials |
| `flatbread whoami`                      | Show who is signed in on this machine |
| `flatbread doctor`                      | Check this machine is ready; print the next step |
| `flatbread setup`                       | Connect the agents installed here |
| `flatbread setup --uninstall`           | Remove exactly what setup added |
| `flatbread share`                       | Review the newest session; Confirm shares it |
| `flatbread share --file <path>`         | The same, for one session file |
| `flatbread pull <id\|url>`              | Print a run's Context Capsule |
| `flatbread pull <id\|url> --out <file>` | Write it to a file instead |
| `flatbread search <words>`              | Find public runs, and your own when signed in |
| `flatbread parse --file <path>`         | Print a session's brief; writes nothing |
| `flatbread adapters`                    | List the harness adapters and their confidence |
| `flatbread mcp`                         | The MCP server setup registers, on stdio |

`flatbread --help` prints every option, and `flatbread --version` the version.
`flatbread doctor --json` and `flatbread whoami --json` print one JSON object for an agent to read.
Exit code 0 means done (doctor: ready; whoami: signed in); 1 means not, with the reason on screen.
