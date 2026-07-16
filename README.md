# Choice India — FinX OpenAPI Documentation

Unofficial Markdown conversion of the Choice FinX **OpenAPI Interface (V1)** documentation.

**API:** OpenAPIInterface_API V1 &nbsp;|&nbsp; **Version:** v1 &nbsp;|&nbsp; **Spec:** Swagger/OpenAPI 2.0

Source: <https://finx.choiceindia.com/api/OpenAPI/Info>

## Contents

- [01-introduction.md](01-introduction.md) — API overview, getting started, encryption note and authentication scheme
- [02-authentication.md](02-authentication.md) — Register, TOTP login, session generation and user profile
- [03-orders-v1.md](03-orders-v1.md) — Order placement / book / positions (V1 — to be deprecated)
- [04-orders-v2.md](04-orders-v2.md) — Order placement / book / positions (V2 — recommended)
- [05-margin.md](05-margin.md) — Margin calculation
- [06-funds.md](06-funds.md) — Funds view
- [07-payments.md](07-payments.md) — Payments, payout and debit funds
- [08-edis.md](08-edis.md) — eDIS verification (CDSL) for non-POA clients
- [09-market-data.md](09-market-data.md) — Touchline / scrip details, market status, chart history
- [10-websocket.md](10-websocket.md) — FINX Interactive Socket: real-time market status, order & trade streaming
- [11-error-codes.md](11-error-codes.md) — Response envelope and HTTP error codes
- [12-appendix.md](12-appendix.md) — All schema definitions

## Endpoint summary

| Group | Endpoints |
| --- | --- |
| Register | 1 |
| Login | 5 |
| Orders (V1) [to be deprecated] | 12 |
| Orders (V2) | 8 |
| Margin | 1 |
| Fund | 2 |
| Payment | 6 |
| EDIS | 2 |
| Graph | 1 |
| Market Status | 1 |
| ScripInfo | 2 |
| **Total** | **41** |

Real-time updates (market status, order & trade streaming) are delivered over the **FINX Interactive Socket** WebSocket — see [10-websocket.md](10-websocket.md).

## Authentication (quick reference)

1. Register the client as an OpenAPI user (`/api/OpenAPI/Register`).
2. Generate an API Key from the FinX website (Profile > Generate API Key).
3. Complete the TOTP login flow to obtain a secret `SessionId`.
4. Send `Authorization: SessionId <your-session-id>` header on every subsequent request.

> Sensitive fields must be encrypted with **AES CBC 256 PKCS7**; the key & IV are shared by Choice in person.
