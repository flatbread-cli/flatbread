# Security

Report a vulnerability privately: on this repository's **Security** tab, choose **Report a
vulnerability**. Please do not open a public issue for it.

Report it here if you find:

- a way to open a run you were not given - a private run, or another account's
- a secret left in an uploaded run that one of Flatbread's rules should have caught
  ([docs/redaction.md](docs/redaction.md) lists them; a kind of secret it has no rule for is a
  redaction-miss issue instead)
- anything `flatbread-cli` uploads before you press Confirm on the review page

Only the latest version on npm is supported: `npm install -g flatbread-cli@latest`.

## If a secret of yours is in a public run

Open the run and press **Manage run**: type the secret into **Hide a word or phrase** (or redact it in
Kept values, if a reviewer kept it), make the run private, or delete it. Then rotate the secret - anyone
could have read it while the run was public.
