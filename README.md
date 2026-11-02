# Omnio Brokers plugin

<img src="assets/logo.png" alt="Omnio Brokers" width="96" />

Connects your assistant (Cursor, Grok Bot) to **Omnio Brokers**, the portfolio platform for Chilean insurance brokerages. It reads the portfolio of the user who authorizes the session and can create leads.

This repository only holds the plugin manifest. The plugin is a hosted remote MCP server:

```
https://api.omnio-brokers.com/mcp
```

Authentication is OAuth 2.1 with dynamic client registration and PKCE. You sign in with your own Omnio account on the Omnio screen; there are no API keys or client secrets to configure.

## What it does

- Identifies the signed-in user and brokerage.
- Searches and opens clients, policies, renewals, claims, overdue installments and leads.
- Returns counts of active policies, policies expiring in 30 days, open claims and overdue installments.
- Creates a lead with an idempotency key (the same key returns the existing lead, no duplicates) and updates a lead's phone, notes or estimated value.

Searches return at most 20 rows, and only data from your brokerage within your scope (the whole brokerage or only your assigned records).

## Tools

| Tool | Purpose |
| --- | --- |
| `get_current_user` | Who you are and which brokerage the session belongs to |
| `search_clients`, `get_client` | Find and open clients |
| `get_client_policies`, `get_client_debt` | A client's policies and outstanding installments |
| `search_policies`, `get_policy` | Find and open policies |
| `get_renewals` | Policies coming up for renewal |
| `search_claims`, `get_claim` | Find and open claims |
| `get_overdue_payments` | Overdue installments |
| `get_portfolio_summary` | Portfolio counts |
| `search_leads`, `get_lead` | Find and open leads |
| `create_lead`, `update_lead` | Create a lead (idempotent) or update phone, notes or estimated value |

## What it does not do

It does not quote policies, open claims, collect payments, show commissions, or switch brokerage. If a producer already escalated a lead to the internal executive, Omnio rejects changes to it.

## Support and legal

- Support: soporte@omnio-brokers.com
- Website: https://omnio-brokers.com
- Privacy policy: https://app.omnio-brokers.com/legal/privacidad
- Terms of service: https://app.omnio-brokers.com/legal/terminos

## En español

Omnio Brokers conecta tu asistente con la cartera de tu corredora de seguros en Omnio: clientes, pólizas, renovaciones, siniestros, cuotas vencidas y leads. Inicias sesión con tu propia cuenta de Omnio. Soporte: soporte@omnio-brokers.com.

## License

MIT. See [LICENSE](LICENSE).
