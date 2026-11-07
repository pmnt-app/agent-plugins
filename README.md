# pmnt for Google Antigravity

pmnt creates payment invoices with an NBU QR code (the QR standard of the
National Bank of Ukraine). This plugin connects Google Antigravity to the pmnt
MCP server at `https://mcp.pmnt.app`. Then the agent can create invoices in
your pmnt account from the chat.

## Requirements

- A pmnt account at [app.pmnt.app](https://app.pmnt.app).
- At least one business with a bank account in that pmnt account.

## Tools

| Tool | What it does | Changes data |
|---|---|---|
| `create_invoice` | Creates an invoice in your pmnt account. Returns a payment link `https://app.pmnt.app/pay/<code>` with an NBU QR code. | Yes: it creates an invoice |
| `list_payees` | Lists your businesses and their bank accounts. | No |
| `list_payment_categories` | Lists the payment categories and purposes for an invoice. | No |

Antigravity asks you before it runs `create_invoice`.

## Sign-in

1. Install the plugin. In the MCP servers of the plugin, click **Authenticate**
   next to `pmnt_invoices`.
2. The pmnt sign-in page (`sso.tulz.dev`) opens in your browser. Sign in with
   your pmnt account and allow **Create invoices**.
3. The Antigravity page shows a code. Click **Copy to Clipboard**, paste the
   code into Antigravity and submit it.

Antigravity keeps the session and refreshes the token. You do not give your
password to Antigravity.

## Example prompts

- "List my businesses and bank accounts in pmnt"
- "Create a pmnt invoice for 500 UAH for consulting services, valid for 7 days"
- "Create a pmnt invoice for a donation. The payer enters the amount."

## What pmnt does not do

- pmnt does not hold or move money, and it does not start transfers. The bank
  of the payer does the transfer.
- pmnt does not ask for card data.

## Links

- Setup guide: <https://pmnt.app/mcp/antigravity>
- Privacy policy: <https://pmnt.app/mcp/privacy>
- Terms of service: <https://pmnt.app/mcp/tos>
- Support: <support@pmnt.app>

## License

Proprietary. See [LICENSE](LICENSE).
