# AIBuilder Marketplace MCP: software pricing dossiers

A free, read-only remote [MCP](https://modelcontextprotocol.io) server for AI agents that research business software before a purchase.

- **Endpoint:** `https://api.aibuildermarketplace.com/mcp` (streamable HTTP)
- **No account, no API key, no install.**
- **Official MCP Registry:** `com.aibuildermarketplace/software-pricing`
- **Docs for agents and developers:** https://aibuildermarketplace.com/agents/

## What it gives your agent

Dossiers on 500+ business-software tools (CRM, help desk, email, payroll, e-commerce apps, AI builders and more), built for one question: *what will this actually cost me, and what is the catch?*

- **Dated prices.** Every price is read on the vendor's own pricing page and carries the date it was read.
- **Cost traps with evidence.** Per-seat pricing, annual commitments, renewal jumps, usage meters and add-ons are flagged, each with the sentence it is based on.
- **Unknown stays unknown.** What we could not confirm is listed as unknown, never guessed.
- **Cost at your team size.** Where a product has computable price rules, the server calculates the cost per plan at a given number of users (or orders, locations, contacts), on monthly or annual billing.
- **Hands-on results.** Where we ran a product ourselves, the record says what passed, what failed and what was not tested.

Ranking is text relevance only, never commission. Vendor links that are affiliate links are disclosed in the record. All tools are read-only: nothing is bought, booked or changed.

## Tools

| Tool | What it does |
|---|---|
| `search_products` | Find products by task or name, with filters (max monthly price, free plan, cost traps to avoid, has price rules). |
| `get_product` | The full record for one product: plans, every cost trap with its evidence, pricing date, unknowns, price rules, vendor link with disclosure. |
| `compare_products` | Compare 2 to 6 products side by side; with a team size, adds the cheapest fitting plan's cost where price rules exist. |
| `get_evidence` | The exact sentences behind a product's cost traps and free-plan flag, with read date and source. |
| `estimate_cost` | Cost of each plan at a team size on monthly or annual billing: monthly equivalent, amount billed, commitment, minimums, add-ons. |
| `cost_at_growth` | The cheapest fitting plan as a team grows, and the points where the best plan changes. |
| `check_choice` | Check one software choice against requirements (team size, billing, budget, commitment) before buying. |
| `build_purchase_dossier` | A purchase file for 1 to 6 candidates against the same requirements. |
| `recheck_dossier` | Re-check an earlier purchase file: which facts changed and which conclusions no longer hold. |
| `get_task_evidence` | What we observed when we ran products ourselves, searchable by task or result. |
| `search_offers` | Reader and vendor offers (discounts, extra credits, longer trials) with evidence, verification status and deadline. |
| `get_offer` | The full record of one offer: eligibility as recorded, claim steps, limits, cost after the offer ends. |
| `check_offer_eligibility` | Whether an offer fits a buyer's situation (new or existing customer, plan, billing term). |
| `compare_offer_costs` | Compare 1 to 3 offers on the same billing term and period. |
| `list_categories` | All categories with their product counts. |

## Connect

**Claude (claude.ai or Claude Desktop):** Settings → Connectors → Add custom connector → URL `https://api.aibuildermarketplace.com/mcp`.

**Claude Code:**

```bash
claude mcp add --transport http aibm-pricing https://api.aibuildermarketplace.com/mcp
```

**Cursor** (`~/.cursor/mcp.json`) and other clients that take a JSON config:

```json
{
  "mcpServers": {
    "aibm-pricing": {
      "url": "https://api.aibuildermarketplace.com/mcp"
    }
  }
}
```

**VS Code** (`.vscode/mcp.json`):

```json
{
  "servers": {
    "aibm-pricing": {
      "type": "http",
      "url": "https://api.aibuildermarketplace.com/mcp"
    }
  }
}
```

## Example prompts

- "Which help desk tools under $20 per agent a month have no annual commitment? Show the evidence."
- "What would Pipedrive cost for 12 users on monthly billing, and where are the add-on costs?"
- "Compare 1Password and Bitwarden for a 25-person team and tell me what changes at 50."
- "Build a purchase dossier for three email marketing tools for 5,000 contacts with a $100 monthly budget."

## Limits, honestly

- Prices are as read on the date shown; vendors change them. Check the vendor's page before you buy. `recheck_dossier` tells you what changed since you built a file.
- Prices are mostly in USD as shown to a US visitor; some vendors show other currencies by region.
- Cost calculations exist only for products with computable price rules; elsewhere the record gives the plans and notes, not a total.
- Hands-on results exist for a minority of products and are labelled with what was and was not tested.
- This is research, not advice. We do not sell software and cannot buy it for you.

## Data and source

- Human-readable versions of the same records: https://aibuildermarketplace.com/
- Open data downloads and JSON API: https://aibuildermarketplace.com/data/ and https://aibuildermarketplace.com/api/v1/
- Research datasets with DOIs on Zenodo: https://aibuildermarketplace.com/research/

## Contact

daniel@aibuildermarketplace.com

## License

Documentation in this repository and the data the server returns: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The server itself is a hosted service; there is no code to install.
