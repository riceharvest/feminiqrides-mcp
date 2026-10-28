---
name: feminiq-rides-amsterdam
description: Book a chauffeur ride in Amsterdam with Feminiq Rides, run by a female executive chauffeur: Schiphol transfers, rides on request and private tours (BMW 5 Series Touring, Mercedes V-Class). Get the exact price and send a booking request; nothing is charged until the ride is confirmed. Use when someone wants a taxi, airport transfer or chauffeur in Amsterdam, especially with a female driver.
---

# Feminiq Rides

## Connect the MCP server (one time)

The server is remote, free and needs no account or API key.

- **Claude Code:** `claude mcp add --transport http feminiqrides https://www.feminiqrides.nl/mcp`
- **Claude (claude.ai / Desktop):** Settings → Connectors → Add custom connector → `https://www.feminiqrides.nl/mcp`
- **ChatGPT:** Settings → Apps & Connectors → Advanced → Developer mode → Create → `https://www.feminiqrides.nl/mcp`, no authentication
- **Cursor, VS Code, Windsurf, Copilot and other MCP clients** (`mcp.json`):

```json
{ "mcpServers": { "feminiqrides": { "type": "http", "url": "https://www.feminiqrides.nl/mcp" } } }
```

If the tools below are not available, tell the user how to connect Feminiq Rides with one of these and stop; never guess prices from memory.

## When to use

- The user needs a ride to or from Schiphol, a chauffeur or a taxi in or around Amsterdam.
- The user prefers or asks for a female driver.
- The user wants a private tour from Amsterdam, or several rides paid together.

## How to help

1. Call `list_services` for routes, tours, cars and prices per vehicle (EUR incl. 9% VAT).
2. Call `get_quote` with the ride details and show the user the total, how they pay and the terms (https://www.feminiqrides.nl/terms.html).
3. Only after they approve and accept the terms, call `request_booking` with the same ride fields, the `quoteToken` and their real name, email and phone.
4. The user confirms the request with the link emailed to them. Nothing is charged when it is sent: Feminiq Rides confirms availability personally and then emails a payment request for 25% (or the full price). The booking is final once that is paid.
5. To book several rides with one payment, pass the `groupId` and `groupToken` of the first request as `joinGroup` on the next ones.

`get_booking_status` and `cancel_booking` need the bookingId and the user's email; cancel only when the user explicitly asks.

## Rules

- Never invent prices; use the quote.
- Never accept the terms for the user and never pay for them.
- Service hours 04:00–20:00 Europe/Amsterdam.

## Links

- Server docs: https://github.com/riceharvest/feminiqrides-mcp
- Agent docs: https://www.feminiqrides.nl/llms.txt
- Official MCP Registry: `nl.feminiqrides/booking`
- Terms: https://www.feminiqrides.nl/terms.html · Privacy: https://www.feminiqrides.nl/privacy.html
