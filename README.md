# Feminiq Rides MCP server

Book Amsterdam chauffeur rides with an AI assistant, with a female driver option: Schiphol transfers, rides on request and private tours (BMW 5 Series Touring, Mercedes V-Class).

Official remote [Model Context Protocol](https://modelcontextprotocol.io) server of **Feminiq Rides** (https://www.feminiqrides.nl/).

| | |
|---|---|
| Endpoint | `https://www.feminiqrides.nl/mcp` |
| Transport | Streamable HTTP (MCP 2026-07-28 and 2025-03-26 to 2025-11-25) |
| Authentication | none |
| Official MCP Registry | `nl.feminiqrides/booking` |

## Tools

- **list_services** (read-only): fixed-price Schiphol routes, private tours and cars with passenger and luggage limits and prices.
- **get_quote** (read-only): exact price and rule check for one ride; returns a signed `quoteToken` valid for 15 minutes. No booking, no email, no payment.
- **request_booking**: sends the quoted ride as a booking request with the customer's name, email and phone, only after the customer approved the price and accepted the Terms. The customer confirms the request through a link emailed to them before the business sees it. Nothing is charged through MCP.

## Connect

- **Claude**: add a custom connector with the endpoint URL (no authentication).
- **ChatGPT** (Developer mode): add a connector with the endpoint URL, authentication none.
- **Cursor / VS Code / any MCP client**:

```json
{ "mcpServers": { "feminiqrides": { "url": "https://www.feminiqrides.nl/mcp" } } }
```

## Links

- Website and booking form: https://www.feminiqrides.nl/
- Agent docs: https://www.feminiqrides.nl/llms.txt
- API (OpenAPI): https://www.feminiqrides.nl/openapi.json
- Terms: https://www.feminiqrides.nl/terms.html · Privacy: https://www.feminiqrides.nl/privacy.html
- Demo: https://www.feminiqrides.nl/media/mcp-demo.mp4

The server itself runs on the business's website; this repository holds its public documentation and listing metadata.
