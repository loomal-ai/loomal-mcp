# @loomal/mcp

> [!WARNING]
> **`@loomal/mcp` is deprecated.** Loomal is now **Mailgent**. Please migrate to
> [`@mailgent/mcp`](https://www.npmjs.com/package/@mailgent/mcp). See the
> [migration guide](https://docs.mailgent.dev/migrate).
>
> This package now ships as a **compatibility shim**: it defaults to
> `https://api.mailgent.dev` and prefers the `MAILGENT_API_KEY` /
> `MAILGENT_API_URL` env vars, while still accepting the legacy
> `LOOMAL_API_KEY` / `LOOMAL_API_URL` names so existing configs keep working.

Identity infrastructure for AI agents — email, credentials, and TOTP in one place.

## Quick Start

Use the new package, `@mailgent/mcp` (recommended):

```json
{
  "mcpServers": {
    "mailgent": {
      "command": "npx",
      "args": ["-y", "@mailgent/mcp"],
      "env": {
        "MAILGENT_API_KEY": "YOUR_API_KEY"
      }
    }
  }
}
```

Get your API key from [console.mailgent.dev](https://console.mailgent.dev).

<details>
<summary>Deprecated: using <code>@loomal/mcp</code></summary>

The legacy package still runs as a shim. It defaults to `api.mailgent.dev` and
accepts either `MAILGENT_API_KEY` or the older `LOOMAL_API_KEY`:

```json
{
  "mcpServers": {
    "loomal": {
      "command": "npx",
      "args": ["-y", "@loomal/mcp"],
      "env": {
        "MAILGENT_API_KEY": "YOUR_API_KEY"
      }
    }
  }
}
```

</details>

## Examples

```
> Send an onboarding email to the new client
> Check my inbox and reply to the latest message
> Store my Stripe API key in the vault
> Get the TOTP code for my AWS account
> Delete the test thread I created earlier
```

## Tools

### Identity

| Tool | Description |
|------|-------------|
| `identity_whoami` | Get identity info — name, email, scopes |

### Email

| Tool | Description |
|------|-------------|
| `mail_send` | Send email |
| `mail_reply` | Reply to a message |
| `mail_list_messages` | List inbox messages |
| `mail_get_message` | Get a specific message |
| `mail_update_labels` | Update message labels |
| `mail_delete_message` | Delete a message |
| `mail_list_threads` | List conversation threads |
| `mail_get_thread` | Get a full thread |
| `mail_delete_thread` | Delete a thread |

### Vault

| Tool | Description |
|------|-------------|
| `vault_list` | List stored credentials |
| `vault_get` | Get a decrypted credential |
| `vault_totp` | Generate a TOTP code (response includes `backupCodesRemaining`) |
| `vault_totp_use_backup` | Atomically consume one TOTP backup code |
| `vault_store` | Store or update a credential (generic — any type) |
| `vault_storeApiKey` | Store an API key (single secret or OAuth client+secret pair) |
| `vault_storeCard` | Store a payment card — encrypted at rest, vault does not process payments |
| `vault_storeShippingAddress` | Store a shipping / mailing address |
| `vault_delete` | Delete a credential |

## Multiple Identities

Each identity is its own MCP server instance:

```json
{
  "mcpServers": {
    "sales-agent": {
      "command": "npx",
      "args": ["-y", "@mailgent/mcp"],
      "env": { "MAILGENT_API_KEY": "loid-sales-key" }
    },
    "support-agent": {
      "command": "npx",
      "args": ["-y", "@mailgent/mcp"],
      "env": { "MAILGENT_API_KEY": "loid-support-key" }
    }
  }
}
```

## Docs

[docs.mailgent.dev](https://docs.mailgent.dev)

## License

MIT
