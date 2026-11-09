# pmnt plugins for AI agents

pmnt creates payment invoices with an NBU QR code (the QR standard of the
National Bank of Ukraine). This repository connects AI agents to the pmnt MCP
server at `https://mcp.pmnt.app`. Then the agent can create invoices in your
pmnt account from the chat.

## Requirements

- A pmnt account at [app.pmnt.app](https://app.pmnt.app).
- At least one business with a bank account in that pmnt account.

## Install

### Claude Code

In a terminal:

```
claude plugin install pmnt --marketplace pmnt-app/agent-plugins
```

Or in a Claude Code session:

```
/plugin install pmnt --marketplace pmnt-app/agent-plugins
```

Then run `/mcp`, select `plugin:pmnt:invoices` and sign in.

### Claude Desktop and claude.ai

1. Open **Customize > Plugins**. Click **Add > Add marketplace** and enter
   `pmnt-app/agent-plugins`.
2. Add the `pmnt` plugin.
3. On the **Connectors** tab of the plugin, click **Connect** and sign in.

### Codex

In the Codex TUI, type `/plugins`, add the marketplace `pmnt-app/agent-plugins`
and install `pmnt`. Codex opens the sign-in page.

From a terminal:

```
codex plugin marketplace add pmnt-app/agent-plugins
codex plugin add pmnt@pmnt-app
```

### VS Code

Open [Install pmnt in VS Code](https://vscode.dev/redirect?url=vscode%3A%2F%2Fchat-plugin%2Finstall%3Fsource%3Dpmnt-app%252Fagent-plugins%26plugin%3Dpmnt)
and confirm the prompts. VS Code adds the marketplace `pmnt-app/agent-plugins`
and installs `pmnt`.

Or run **Chat: Open Customizations**, add the marketplace
`pmnt-app/agent-plugins` and install `pmnt`. Agent plugins need the
`chat.plugins.enabled` setting.

### GitHub Copilot CLI

```
copilot plugin marketplace add pmnt-app/agent-plugins
copilot plugin install pmnt@pmnt-app
```

Then start a new `copilot` session. VS Code also finds the plugins that
Copilot CLI installs.

If `copilot plugin` gives "Invalid command format", your Copilot CLI is too
old. Update it, for example with `npm install -g @github/copilot@latest`.

### Google Antigravity

```
agy plugin install https://github.com/pmnt-app/agent-plugins
```

Then click **Authenticate** next to `pmnt_invoices`. Setup guide:
<https://pmnt.app/mcp/antigravity>

## Sign-in

The pmnt sign-in page (`sso.tulz.dev`) opens in your browser. Sign in with
your pmnt account and allow **Create invoices**. You do not give your password
to the agent. The agent keeps the session and refreshes the token.

## Tools

| Tool | What it does | Changes data |
|---|---|---|
| `create_invoice` | Creates an invoice in your pmnt account. Returns a payment link `https://app.pmnt.app/pay/<code>` with an NBU QR code. | Yes: it creates an invoice |
| `list_payees` | Lists your businesses and their bank accounts. | No |
| `list_payment_categories` | Lists the payment categories and purposes for an invoice. | No |

## Example prompts

- "List my businesses and bank accounts in pmnt"
- "Create a pmnt invoice for 500 UAH for consulting services, valid for 7 days"
- "Create a pmnt invoice for a donation. The payer enters the amount."

## What pmnt does not do

- pmnt does not hold or move money, and it does not start transfers. The bank
  of the payer does the transfer.
- pmnt does not ask for card data.

## Files

| File | Read by |
|---|---|
| `.claude-plugin/marketplace.json` | Claude Code, Claude Desktop, claude.ai, Codex, VS Code and GitHub Copilot CLI. It lists the plugin in `plugins/pmnt`. |
| `plugins/pmnt/.claude-plugin/plugin.json`, `plugins/pmnt/.mcp.json` | Claude Code, Claude Desktop, claude.ai |
| `plugins/pmnt/plugin.json`, `plugins/pmnt/mcp.json` ([Agent Plugins](https://agent-plugins.org) 1.0.0) | Codex, VS Code and GitHub Copilot CLI |
| `.antigravity-plugin/plugin.json`, `mcp_config.json` | Google Antigravity (it installs the repository root) |

The files hold only the public URL of the MCP server. They hold no client IDs,
secrets or tokens.

## Links

- Privacy policy: <https://pmnt.app/mcp/privacy>
- Terms of service: <https://pmnt.app/mcp/tos>
- Support: <support@pmnt.app>

## License

Proprietary. See [LICENSE](LICENSE).
