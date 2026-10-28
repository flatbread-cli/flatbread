# What Flatbread removes on your machine

`flatbread share` scans the session on your machine before anything uploads - no network call, no
model - and replaces every match with a token.

| What | Replaced with |
| --- | --- |
| AWS access key id | `«REDACTED:aws_access_key»` |
| PEM private key block | `«REDACTED:private_key»` |
| GitHub token | `«REDACTED:github_token»` |
| GitLab personal access token | `«REDACTED:gitlab_token»` |
| Google API key | `«REDACTED:google_api_key»` |
| Google OAuth access token | `«REDACTED:google_oauth_token»` |
| Stripe live or webhook secret | `«REDACTED:stripe_key»` |
| npm access token | `«REDACTED:npm_token»` |
| Supabase secret key or access token | `«REDACTED:supabase_token»` |
| Vercel token | `«REDACTED:vercel_token»` |
| Anthropic API key | `«REDACTED:anthropic_key»` |
| OpenAI-style API key | `«REDACTED:openai_key»` |
| Slack token | `«REDACTED:slack_token»` |
| JWT | `«REDACTED:jwt»` |
| Login inside a connection URL | `«REDACTED:db_credentials»` |
| Secret in a URL query | `«REDACTED:url_secret»` |
| Bearer header value | `«REDACTED:bearer_token»` |
| Home directory username | `«REDACTED:user»` |
| Private network address | `«REDACTED:private_ip»` |
| Internal hostname | `«REDACTED:internal_host»` |
| Secret assigned on one line | `«REDACTED:secret»` |
| Random-looking string (a key with no known prefix) | `«REDACTED:high_entropy»` |
| Email address | `«REDACTED:email»` |
| Value of a credential-named field | `«REDACTED:secret»` |

It also replaces this machine's username wherever it appears as a word (`«REDACTED:user»`), and any
word or phrase of your own: `flatbread share --redact <word>`, or add it on the review page
(`«REDACTED:custom»`).

Everything else in the session is sent when you press Confirm: your prompts, the agent's messages,
the commands it ran, what they printed and the diffs it made. The review page shows all of it, and
every replacement, before you press Confirm, and you can hide anything more there. On a run you already
shared, its Manage run button can hide another word or phrase, make it private or delete it; a
redaction can be added, never undone.

A pattern can only find what it has a pattern for. Read the review page before you confirm, and if
Flatbread missed a secret, report it with the redaction-miss issue form - describe its shape, never paste it.
