# Gmail MCP — Email Operations Guide

## Available tools

The `user-gmail` MCP exposes these tools:

| Tool | Purpose |
|------|---------|
| `gmail_search` | Search emails by query (same syntax as Gmail search bar) |
| `gmail_get_email` | Read a specific email by ID |
| `gmail_send_email` | Compose and send a new email |
| `gmail_reply_to_email` | Reply to an existing thread |
| `gmail_get_labels` | List all Gmail labels |

## Composing emails

When sending or replying:

- **To field** accepts comma-separated emails: `alice@example.com, bob@example.com`
- **HTML is supported** in the body — use it for formatting tables, links, and emphasis
- Always confirm the recipient and subject with the user before sending
- For replies, quote the relevant part of the original message

## Search syntax

Gmail search queries work exactly like the Gmail web UI:

```
from:alice@example.com after:2026/01/01 has:attachment
subject:"weekly report" is:unread
label:important newer_than:7d
```

Common operators:
- `from:`, `to:`, `cc:`, `bcc:` — filter by participant
- `subject:` — filter by subject line
- `after:`, `before:` — date range (YYYY/MM/DD)
- `newer_than:`, `older_than:` — relative dates (e.g. `7d`, `1m`)
- `has:attachment` — only emails with attachments
- `is:unread`, `is:starred`, `is:important` — status filters
- `label:` — filter by label
- `filename:` — search attachment filenames

## Best practices

1. **Always search before composing** — if the user asks to "reply to X's email",
   search for it first rather than asking for the email ID.
2. **Summarise long threads** — when reading a thread, give the user a concise
   summary before presenting the full content.
3. **Draft confirmation** — show the user what you're about to send and ask for
   confirmation before calling `gmail_send_email`.
4. **Batch operations** — if multiple emails need the same action (label, archive),
   describe the batch and confirm before executing.
