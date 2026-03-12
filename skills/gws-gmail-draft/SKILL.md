---
name: gws-gmail-draft
version: 1.0.0
description: "Gmail: Create an email draft (drafts-only mode)."
metadata:
  openclaw:
    category: "productivity"
    requires:
      bins: ["gws"]
    cliHelp: "gws gmail +draft --help"
---

# gmail +draft

> **PREREQUISITE:** Read `../gws-shared/SKILL.md` for auth, global flags, and security rules. If missing, run `gws generate-skills` to create it.

Create an email draft. This is a **drafts-only** fork — all email composition creates drafts that must be reviewed and sent manually from Gmail.

## Usage

```bash
gws gmail +draft [--profile <NAME>] --to <EMAILS> --subject <SUBJECT> --body <TEXT>
```

## Flags

| Flag | Required | Default | Description |
|------|----------|---------|-------------|
| `--to` | yes | — | Recipient email address(es), comma-separated |
| `--subject` | yes | — | Email subject |
| `--body` | yes | — | Email body (plain text) |
| `--cc` | — | — | CC email address(es), comma-separated |
| `--bcc` | — | — | BCC email address(es), comma-separated |
| `--profile` | — | — | Account profile to use (see gws-shared for setup) |
| `--dry-run` | — | — | Show the request that would be built without executing it |

## Examples

```bash
gws gmail +draft --to alice@example.com --subject 'Hello' --body 'Hi Alice!'
gws gmail +draft --profile work --to alice@example.com --subject 'Hello' --body 'Hi!'
gws gmail +draft --to alice@example.com --subject 'Hello' --body 'Hi!' --cc bob@example.com
gws gmail +draft --to alice@example.com --subject 'Hello' --body 'Hi!' --bcc secret@example.com
```

## Tips

- Creates a draft in your Gmail Drafts folder. You must manually send from Gmail.
- Handles RFC 2822 formatting and base64 encoding automatically.
- This fork does NOT support sending emails directly. The `+send` command has been removed.

> [!CAUTION]
> This is a **write** command — confirm with the user before executing.

## See Also

- [gws-shared](../gws-shared/SKILL.md) — Global flags and auth
- [gws-gmail](../gws-gmail/SKILL.md) — All draft, read, and manage email commands
