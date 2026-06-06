# @loomal/mcp — deprecated

> [!WARNING]
> **Loomal is now [Mailgent](https://mailgent.dev).** This package is deprecated — please migrate to **[`@mailgent-dev/mcp`](https://www.npmjs.com/package/@mailgent-dev/mcp)**.

`@loomal/mcp` now ships as a compatibility shim: it defaults to `https://api.mailgent.dev` and prefers `MAILGENT_API_KEY` / `MAILGENT_API_URL` (still accepting the legacy `LOOMAL_*` names). No new features will be added here.

## Migrate

Update your MCP server config:

```json
{
  "command": "npx",
  "args": ["-y", "@mailgent-dev/mcp"],
  "env": { "MAILGENT_API_KEY": "loid-..." }
}
```

- Docs: <https://docs.mailgent.dev>
- Migration guide: <https://docs.mailgent.dev/migrate>

## License
MIT
