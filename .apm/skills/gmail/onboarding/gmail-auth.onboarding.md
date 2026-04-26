---
id: gmail-auth
name: Authenticate Gmail MCP
type: interactive
completed-when:
  - file-exists: ~/.gmail-mcp/credentials.json
---

# Authenticate Gmail MCP

The Gmail MCP server needs OAuth credentials to access the user's inbox.

## Steps

1. Check if `~/.gmail-mcp/credentials.json` exists
2. If not, the user needs to run the Gmail MCP once manually to trigger
   the OAuth flow:

```bash
npx -y @shinzolabs/gmail-mcp
```

3. Follow the browser prompt to grant Gmail access
4. Credentials are saved to `~/.gmail-mcp/`

## Verification

```bash
ls ~/.gmail-mcp/credentials.json
```

The file should exist after successful authentication.
