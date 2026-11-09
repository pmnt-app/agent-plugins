# pmnt plugin for Claude and Codex

This plugin connects the agent to the pmnt MCP server at
`https://mcp.pmnt.app`. The agent can then create invoices with an NBU QR code
in your pmnt account.

- Tools: `create_invoice` (creates an invoice), `list_payees` and
  `list_payment_categories` (read only).
- Sign-in: the pmnt sign-in page (`sso.tulz.dev`) opens in your browser. Allow
  **Create invoices**. You do not give your password to the agent.
- Requirements: a pmnt account at <https://app.pmnt.app> with a business and a
  bank account.

Install in Claude Code:

```
/plugin install pmnt --marketplace pmnt-app/agent-plugins
```

Install in Codex:

```
codex plugin marketplace add pmnt-app/agent-plugins
codex plugin add pmnt@pmnt-app
```

Other clients and links: <https://github.com/pmnt-app/agent-plugins>
