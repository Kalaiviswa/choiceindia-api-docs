# FINX Interactive Socket (WebSocket API)

**Technical Reference v1.0 — May 2026**

The FINX Interactive Socket provides a persistent, real-time WebSocket connection for receiving market data, order status updates, trade confirmations and market-level events. Communication is bidirectional and message-driven using JSON payloads.

## 1. Overview

| Property | Value |
| --- | --- |
| Protocol | WebSocket Secure (`wss://`) |
| Host | `finxsocket.choiceindia.com` |
| Auth mechanism | JWT token (RS256) passed as a URL query parameter |
| Message format | JSON |
| Keep-alive timeout | 30 seconds (heartbeat check every 1 second) |

---

## 2. Authentication & Connection

### 2.1 Token source — Logon response

> ⚠ **IMPORTANT:** The JWT token used in the WebSocket URL is **not** generated independently. It is the access token returned by the **Logon (2FA) API** response. Complete the authentication flow first, extract the token from the Logon response, then supply it as the `token` query parameter when opening the WebSocket connection.

| Step | Action |
| --- | --- |
| 1 | Call the Logon / 2FA authentication API (see [02-authentication.md](02-authentication.md)) |
| 2 | Parse the JWT access token from the Logon API response |
| 3 | Append the token as `?token=<JWT>` to the WebSocket URL |
| 4 | Open the WebSocket connection — the server validates the token |

### 2.2 WebSocket connection URL

Connection endpoint format:

```
wss://finxsocket.choiceindia.com/ws/?token=<JWT_TOKEN_FROM_LOGON_RESPONSE>
```

Example URL (token abbreviated for display):

```
wss://finxsocket.choiceindia.com/ws/?token=eyJhbGciOiJSUzI1NiIsImtpZCI6Ikk...
```

### 2.3 JWT token claims

The token is signed with **RS256** (RSA + SHA-256). Key claims in the payload:

| Claim | Example value | Description |
| --- | --- | --- |
| `iat` | `1778202094` | Issued-at timestamp (Unix epoch) |
| `nbf` | `1778202094` | Not-valid-before timestamp |
| `exp` | `1778230894` | Expiry timestamp (Unix epoch) — ~8 hrs |
| `UserId` | `X123838` | Authenticated user ID |
| `DeviceId` | `a=fingerprint:sha-256 03:E6:...` | Device fingerprint of the client |
| `SessionId` | `01KR2HNB62HJH7XBGBN0MKA8MM` | Unique session identifier |
| `iss` | `FINX` | Issuer — always `FINX` |

### 2.4 Connection error codes

| Scenario | HTTP status | Description / reason |
| --- | --- | --- |
| Token expired | `401 Unauthorized` | Token has expired and is no longer valid |
| Invalid token used (e.g. FT access token) | `401 Unauthorized` | Token is not recognized or does not match expected usage |
| Max connections exceeded | `429 Too Many Requests` | Server has reached the connection limit for this account |
| Server-side exception | `500 Internal Server Error` | Unexpected error occurred on the server side |

---

## 3. Keep-Alive / Heartbeat

The connection uses a heartbeat mechanism to detect idle or dead connections:

| Parameter | Value |
| --- | --- |
| Timeout | 30 seconds |
| Heartbeat check interval | Every 1 second |
| Client keep-alive signal | Send: `2` |
| Server keep-alive response | Responds: `3` |

If no heartbeat is received within 30 seconds, the server closes the connection. The client must send the value `2` as a plain text/integer message; the server acknowledges with `3`.

---

## 4. Message Types

All messages are JSON objects. Each message contains a `MessageType` field identifying the category of event.

| MessageType | Description |
| --- | --- |
| `MKT_STAT` | Market status event — segment open/close notifications |
| `ORD_NRML` | Order status update for normal orders |
| `TRD_MSG` | Trade confirmation / execution update |

---

## 5. Market Status — `MKT_STAT`

### 5.1 Request payload

```json
{
  "MessageType": "MKT_STAT",
  "MsgHeader": {
    "ManagerID": "20"
  },
  "Data": {
    "EventType": "6",
    "Segment": "1"
  }
}
```

### 5.2 EventType values

| EventType | Description |
| --- | --- |
| 1 | Normal Market Open |
| 2 | Normal Market Close |
| 3 | Pre-Open |
| 4 | Pre-Open Close |
| 5 | Auction Market Open |
| 6 | Auction Market Close |
| 7 | Auction Market Open (Secondary) |
| 8 | Post Trade / Close Open |
| 9 | Post Trade / Close Close |
| 10 | Special Market Open |
| 11 | Special Market Close |

### 5.3 Segment values

| Segment ID | Exchange / segment |
| --- | --- |
| 1 | NSE Cash |
| 2 | NSE Derivatives |
| 3 | BSE Cash |
| 4 | BSE Derivatives |
| 5 | MCX Futures |
| 6 | MCX Spot |
| 7 | NCDEX Futures |
| 8 | NCDEX Spot |
| 11 | MCX SX Currency Futures |
| 12 | MCX SX Currency Spot |
| 13 | NSECDS Futures |
| 14 | NSECDS Spot |
| 15 | MSX Cash |
| 16 | MSX Derivatives |
| 25 | BSE OFS |
| 33 | NSE OFS |
| 34 | ICEX |
| 38 | BSECDS Currency |

### 5.4 Sample response — market status

```json
{
  "MessageType": "MKT_STAT",
  "MsgHeader": { "ManagerID": "1" },
  "Data": {
    "EventType": "2",
    "Segment": "13"
  }
}
```

→ Segment `13` (NSECDS Futures) has performed a Normal Market Close (`EventType` 2).

---

## 6. Order Status — `ORD_NRML`

### 6.1 Message payload — field reference

| Field | Sample value | Description |
| --- | --- | --- |
| `MessageType` | `ORD_NRML` | Message type identifier |
| `OrderNumber` | `1300000049665550` | Unique exchange-assigned order number |
| `UniqueCode` | `260508000093968` | Client-side unique order reference code |
| `Symbol` | `RBA` | Scrip / stock symbol |
| `InstrumentName` | `RBA-EQ` | Full instrument name including segment suffix |
| `Series` | `EQ` | Exchange series (e.g. EQ, BE, N) |
| `ScripCode` | `1494` | Exchange-specific scrip code |
| `Exchange` | `1` | Exchange identifier (1 = NSE) |
| `Buy_Sell` | `2` | Trade direction: 1 = Buy, 2 = Sell |
| `OrderType` | `2.0` | 1 = Limit, 2 = Market |
| `OrderOriginalQty` | `1.0` | Original quantity placed in the order |
| `PendingQty` | `1.0` | Quantity still pending execution |
| `TradedQTY` | `0` | Quantity traded so far |
| `OrderPrice` | `0.0` | Limit price; 0 for market orders |
| `TriggerPrice` | `0.0` | Stop-loss trigger price; 0 if not applicable |
| `OrderStatus` | `5.0` | Status code (see [6.2](#62-orderstatus-code-reference)) |
| `OrderValidity` | `1` | 1 = Day, 2 = IOC, etc. |
| `Product` | `D` | D = Delivery (CNC), M = Margin (MIS) |
| `ProCli` | `1` | 1 = Client order, 2 = Proprietary |
| `UCC` | `X123838` | Unique client code |
| `UserID` | `X123838` | Logged-in user ID |
| `OrderEntryTime` | `08-May-2026 11:55:20` | Timestamp when order was placed |
| `LastModifiedTime` | `08-May-2026 11:55:20` | Timestamp of last modification |
| `InitiatedBy` | `MOBILE` | Channel through which order was placed |
| `Misc` | `open` | Miscellaneous status description |
| `ManagerID` | `27` | Internal manager / broker ID |
| `MessageSequenceNumber` | `0` | Sequence number of the message |
| `DQ` / `DQRemaining` | `0.0` | Disclosed quantity and remaining disclosed qty |
| `Days` | `0` | Number of days for GTD orders |
| `GTDOrderStatus` | `0.0` | Good-till-date order status flag |
| `StrikePrice` / `Option_Type` | `0.0` / blank | Used for F&O; blank/0 for equity |
| `SpreadFlag` / `SpreadPrice` | `0.0` | Spread order indicators |
| `LegIndicator` | blank | Leg reference for spread/combo orders |
| `AMOOrderID` | blank | After-market order identifier (if applicable) |
| `CP_ID` | blank | Counter-party ID (institutional use) |
| `PartCode` | blank | Participant code |
| `UserRemarks` | blank | Free-text remarks entered by user |
| `MarketType` | `0.0` | Market type identifier |

### 6.2 OrderStatus code reference

| OrderStatus | Meaning |
| --- | --- |
| 1 | New / Placed |
| 2 | Partially Traded |
| 3 | Fully Traded / Completed |
| 4 | Cancelled |
| 5 | Open / Pending (awaiting execution) |
| 6 | Rejected |
| 7 | Modified |

---

## 7. Trade Update — `TRD_MSG`

### 7.1 Message payload — field reference

| Field | Sample value | Description |
| --- | --- | --- |
| `MessageType` | `TRD_MSG` | Message type identifier |
| `TradeNumber` | `605061857` | Unique exchange-assigned trade number |
| `OrderNumber` | `1300000049665550` | Corresponding order number |
| `CliOrderNumber` | `0.0` | Client-side order number (if assigned) |
| `Symbol` | `RBA-EQ` | Full instrument name |
| `Series` | `EQ` | Exchange series |
| `ScripCode` | `1494.0` | Exchange scrip code |
| `Exchange` | `1.0` | Exchange identifier (1 = NSE) |
| `Buy_Sell` | `2` | 1 = Buy, 2 = Sell |
| `TradeQty` | `1` | Quantity executed in this trade |
| `TradedPrice` | `6723` | Price at which the trade was executed |
| `OrderOriginalQty` | `1.0` | Original order quantity |
| `PendingQty` | `0` | Remaining quantity after this trade |
| `QuantityTradedToday` | `1.0` | Cumulative traded quantity for the day |
| `OrderType` | `2.0` | 1 = Limit, 2 = Market |
| `TradeTime` | `2026-05-08 11:55:20` | Timestamp of trade execution (ISO format) |
| `OrderTime` | `08-May-2026 11:55:20` | Timestamp when the order was placed |
| `OrderLastModifiedTime` | `08-May-2026 11:55:20` | Timestamp of last order modification |
| `TradeTimeStamp` | `2026-05-08 11:55:20` | Duplicate trade timestamp (ISO format) |
| `UniqueCode` | `260508000093968` | Client-side unique reference code |
| `UCC` | `X123838` | Unique client code |
| `UserID` | `X123838` | Logged-in user ID |
| `ManagerID` | `27.0` | Internal broker / manager ID |
| `Product` | `D` | D = Delivery, M = Margin |
| `ProCli` | `1` | 1 = Client, 2 = Proprietary |
| `DQ` / `DQRemaining` | `0` | Disclosed quantity fields |
| `StrikePrice` / `Option_Type` | `0.0` / blank | F&O fields; blank/0 for equity |
| `SpreadFlag` / `SpreadPrice` | `0.0` | Spread order fields |
| `LegIndicator` | `0` | Leg reference for spread/combo orders |
| `CP_ID` | blank | Counter-party ID |
| `InstrumentName` | blank | Full instrument name (may be blank in trade messages) |
| `InitiatedBy` / `ModifiedBy` | blank | User who initiated or modified the order |
| `Days` | `0.0` | GTD days parameter |
| `MessageSequenceNumber` | `0.0` | Message sequence reference |
| `OrderPrice` | `0.0` | Limit order price (0 for market orders) |
| `UserRemarks` / `Misc` | blank | Free-text fields |

---

## 8. Exchange & Segment Reference

The `Exchange` field in order and trade messages uses the following numeric identifiers:

| Exchange ID | Exchange name |
| --- | --- |
| 1 | NSE (National Stock Exchange) |
| 2 | BSE (Bombay Stock Exchange) |
| 3 | MCX (Multi Commodity Exchange) |
| 4 | NCDEX (National Commodity & Derivatives Exchange) |
| 5 | MCX-SX / MSX (Currency Exchange) |

---

## 9. Connection Flow Summary

| Step | Action |
| --- | --- |
| 1 | Client calls the Logon / 2FA API with credentials |
| 2 | Logon response returns a JWT access token (RS256 signed) |
| 3 | Client opens WebSocket: `wss://finxsocket.choiceindia.com/ws/?token=<JWT>` |
| 4 | Server validates token — connection accepted or rejected (401 / 429 / 500) |
| 5 | Client sends keep-alive value `2` every <30 seconds; server responds with `3` |
| 6 | Server pushes real-time messages: `MKT_STAT`, `ORD_NRML`, `TRD_MSG` |

---

## 10. Revision History

| Version | Date | Author | Changes |
| --- | --- | --- | --- |
| 1.0 | 08-May-2026 | FINX Platform Team | Initial document creation |

---

*Source: FINX Interactive Socket API — Technical Reference v1.0 (Choice | Confidential).*
