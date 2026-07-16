# Orders (V2)

The recommended order-management endpoints. Includes order placement, modification, cancellation, order book, trade book and net position.

### API for New order (V2)

```
POST /api/OpenAPI/V2/NewOrder
```

**Operation ID:** `OpenAPIV2_NewOrder`

**Description**

```text
Description

    This API use to place order in particular segment with proper request options.

Parameters

    Price related fields should be in Paisa (In multiples of 100)

    OrderType:  RL_LIMIT, RL_MKT,SL_LIMIT, SL_MKT
    
        RL_LIMIT : Regular limit order, Price required, Trigger price should be zero
        RL_MKT : Regular market order, Price and Trigger price both should be zero
        SL_LIMIT : Stop loss market order, Price and Trigger price both required
        SL_MKT : Stop loss market order, Price should be 0 and Trigger price required
    
    BS : 1 for Buy 2 for Sell
    
    Validity : 1 for Day, 4 for IOC, 11 for GTD/GTC (only NSE Eq and BSE Eq)
    
    GTD Days required for GTD orders, min 2, max 999
    
    For GTC orders Validity = 11, GTD Days = 999
    
    ProductType: M for Margin/Intraday, D for Delivery, AM for AMO Margin for Equity segments and AMO Intraday for Derivative Segments, AD for AMO Delivery for Equity Segments and AMO CARRYFORWARD for Derivative Segments
    
    RequestType: 1 for entry, 2 for modification,3 for cancellation
    
    IsEdisReq: true for Client POAStatus is false, false for Client POAStatus is true
    
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
    
Segment Master ID's

    NSE-CASH: 1
    
    NSE-DERIVATIVES: 2
    
    BSE-CASH: 3
    
    BSE-DERIVATIVES: 4
    
    MCX-DERIVATIVES (COMMODITIES): 5
    
    MCX-SPOT (COMMODITIES): 6
    
    NCDEX-DERIVATIVES (COMMODITIES): 7
    
    NCDEX-SPOT (COMMODITIES): 8
    
    NSECDS-DERIVATIVES (CURRENCIES): 13
    
    NSECDS-SPOT (CURRENCIES): 14
```

**Consumes:** `application/json`, `text/json`, `application/xml`, `text/xml`, `application/x-www-form-urlencoded`  
**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Request Body**

Schema: **`NewOrderRequestV2`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `SegmentId` | integer (int32) | No |  |
| `Token` | integer (int32) | No |  |
| `OrderType` | string | No |  |
| `BS` | integer (int32) | No |  |
| `Qty` | integer (int32) | No |  |
| `DisclosedQty` | integer (int32) | No |  |
| `Price` | integer (int64) | No |  |
| `TriggerPrice` | integer (int64) | No |  |
| `Validity` | integer (int32) | No |  |
| `ProductType` | string | No |  |
| `IsEdisReq` | boolean | No |  |
| `Remarks` | string | No |  |
| `ModeTyp` | string | No |  |
| `Mode` | integer (int32) | No |  |
| `DeviceId` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Modify Order (V2)

```
POST /api/OpenAPI/V2/ModifyOrder
```

**Operation ID:** `OpenAPIV2_ModifyOrder`

**Description**

```text
Description

    This API use to modify the placed order and will update the order in the system.

Parameters

    Price related fields should be in Paisa (In multiples of 100)

    OrderType:  RL_LIMIT, RL_MKT,SL_LIMIT, SL_MKT
    
        RL_LIMIT : Regular limit order, Price required, Trigger price should be zero
        RL_MKT : Regular market order, Price and Trigger price both should be zero
        SL_LIMIT : Stop loss market order, Price and Trigger price both required
        SL_MKT : Stop loss market order, Price should be 0 and Trigger price required
    
    BS : 1 for Buy 2 for Sell
    
    Validity : 1 for Day, 4 for IOC
    
    ProductType: M for Margin/Intraday, D for Delivery, AM for AMO Margin for Equity segments and AMO Intraday for Derivative Segments, AD for AMO Delivery for Equity Segments and AMO CARRYFORWARD for Derivative Segments
    
    Qty: Pending Quantity needs to be passed
    
    RequestType: 1 for entry, 2 for modification,3 for cancellation
    
    IsEdisReq: true for Client POAStatus is false, false for Client POAStatus is true
    
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
    
Segment Master ID's

    NSE-CASH: 1
    
    NSE-DERIVATIVES: 2
    
    BSE-CASH: 3
    
    BSE-DERIVATIVES: 4
    
    MCX-DERIVATIVES (COMMODITIES): 5
    
    MCX-SPOT (COMMODITIES): 6
    
    NCDEX-DERIVATIVES (COMMODITIES): 7
    
    NCDEX-SPOT (COMMODITIES): 8
    
    NSECDS-DERIVATIVES (CURRENCIES): 13
    
    NSECDS-SPOT (CURRENCIES): 14
```

**Consumes:** `application/json`, `text/json`, `application/xml`, `text/xml`, `application/x-www-form-urlencoded`  
**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Request Body**

Schema: **`ModifyOrderRequestV2`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `ClientOrderNo` | string | No |  |
| `TradedQty` | integer (int32) | No |  |
| `ModeTyp` | string | No |  |
| `SegmentId` | integer (int32) | No |  |
| `Token` | integer (int32) | No |  |
| `OrderType` | string | No |  |
| `BS` | integer (int32) | No |  |
| `Qty` | integer (int32) | No |  |
| `DisclosedQty` | integer (int32) | No |  |
| `Price` | integer (int64) | No |  |
| `TriggerPrice` | integer (int64) | No |  |
| `Validity` | integer (int32) | No |  |
| `ProductType` | string | No |  |
| `IsEdisReq` | boolean | No |  |
| `Remarks` | string | No |  |
| `Mode` | integer (int32) | No |  |
| `DeviceId` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Cancel Order (V2)

```
POST /api/OpenAPI/V2/CancelOrder
```

**Operation ID:** `OpenAPIV2_CancelOrder`

**Description**

```text
Description

    This API use to cancel the placed order.

Parameters

    Price related fields should be in Paisa (In multiples of 100)    

    ClientOrderNo: Alphanumeric ClientOrderId recieved in Orderbook
    
    RequestType: 1 for entry, 2 for modification,3 for cancellation
    
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
    
Segment Master ID's

    NSE-CASH: 1
    
    NSE-DERIVATIVES: 2
    
    BSE-CASH: 3
    
    BSE-DERIVATIVES: 4
    
    MCX-DERIVATIVES (COMMODITIES): 5
    
    MCX-SPOT (COMMODITIES): 6
    
    NCDEX-DERIVATIVES (COMMODITIES): 7
    
    NCDEX-SPOT (COMMODITIES): 8
    
    NSECDS-DERIVATIVES (CURRENCIES): 13
    
    NSECDS-SPOT (CURRENCIES): 14
```

**Consumes:** `application/json`, `text/json`, `application/xml`, `text/xml`, `application/x-www-form-urlencoded`  
**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Request Body**

Schema: **`CancelOrderRequestV2`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `ClientOrderNo` | string | No |  |
| `SegmentId` | integer (int32) | No |  |
| `ModeTyp` | string | No |  |
| `Mode` | integer (int32) | No |  |
| `DeviceId` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for OrderBook (V2)

```
GET /api/OpenAPI/V2/OrderBook
```

**Operation ID:** `OpenAPIV2_OrderBook`

**Description**

```text
Description

    This API use to get Orderbook of particular Client. Price related fields will be in Rupee

Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
   
Order Status
    
    CLIENT XMITTED : Order sent from client, confirmation awaited
    GATEWAY XMITTED : Order sent from Gateway, confirmation awaited
    OMS XMITTED : Order sent from OMS, confirmation awaited
    EXCHANGE XMITTED : Order sent from Exchange, confirmation awaited
    PENDING : Order confirmed from exchange
    CANCELLED : Order cancelled
    EXECUTED : Order Traded
    GATEWAY REJECT : Order rejected by gateway
    OMS REJECT : Order rejected by oms
    ORDER ERROR : Order rejected from exchange
    FROZEN : Order rejected from exchange (The order will go for a freeze if the quantity is greater than the freeze quantity determined by NSE)
    A.ACCEPT [ADMINACCEPT]
    A.REJECT [ADMINREJECT]
    A.MODIFY [ADMINMODIFY]
    A.CANCEL [ADMINCANCEL]
    AMO SUBMITTED : AMO order submitted successfully
    AMO CANCELLED : AMO order cancelled successfully

Segment Master ID's

    NSE-CASH: 1
    
    NSE-DERIVATIVES: 2
    
    BSE-CASH: 3
    
    BSE-DERIVATIVES: 4
    
    MCX-DERIVATIVES (COMMODITIES): 5
    
    MCX-SPOT (COMMODITIES): 6
    
    NCDEX-DERIVATIVES (COMMODITIES): 7
    
    NCDEX-SPOT (COMMODITIES): 8
    
    NSECDS-DERIVATIVES (CURRENCIES): 13
    
    NSECDS-SPOT (CURRENCIES): 14
```

**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for OrderBookByOrderNo (V2)

```
GET /api/OpenAPI/V2/OrderBookByOrderNo/{OrderNo}
```

**Operation ID:** `OpenAPIV2_OrderBook`

**Description**

```text
Description

    This API use to get Orderbook of particular Client OrderNo.

Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
   
Order Status
    
    CLIENT XMITTED : Order sent from client, confirmation awaited
    GATEWAY XMITTED : Order sent from Gateway, confirmation awaited
    OMS XMITTED : Order sent from OMS, confirmation awaited
    EXCHANGE XMITTED : Order sent from Exchange, confirmation awaited
    PENDING : Order confirmed from exchange
    CANCELLED : Order cancelled
    EXECUTED : Order Traded
    GATEWAY REJECT : Order rejected by gateway
    OMS REJECT : Order rejected by oms
    ORDER ERROR : Order rejected from exchange
    FROZEN : Order rejected from exchange (The order will go for a freeze if the quantity is greater than the freeze quantity determined by NSE)
    A.ACCEPT [ADMINACCEPT]
    A.REJECT [ADMINREJECT]
    A.MODIFY [ADMINMODIFY]
    A.CANCEL [ADMINCANCEL]
    AMO SUBMITTED : AMO order submitted successfully
    AMO CANCELLED : AMO order cancelled successfully

Segment Master ID's

    NSE-CASH: 1
    
    NSE-DERIVATIVES: 2
    
    BSE-CASH: 3
    
    BSE-DERIVATIVES: 4
    
    MCX-DERIVATIVES (COMMODITIES): 5
    
    MCX-SPOT (COMMODITIES): 6
    
    NCDEX-DERIVATIVES (COMMODITIES): 7
    
    NCDEX-SPOT (COMMODITIES): 8
    
    NSECDS-DERIVATIVES (CURRENCIES): 13
    
    NSECDS-SPOT (CURRENCIES): 14
```

**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Parameters**

| Name | In | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `OrderNo` | path | string | Yes |  |

**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for OrderBookV2 (V2)

```
GET /api/OpenAPI/V2/OrderBookV2
```

**Operation ID:** `OpenAPIV2_OrderBookV2`

**Description**

```text
Description

    This API use to get Orderbook of particular Client. Price related fields will be in Paisa

Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
   
Order Status
    
    CLIENT XMITTED : Order sent from client, confirmation awaited
    GATEWAY XMITTED : Order sent from Gateway, confirmation awaited
    OMS XMITTED : Order sent from OMS, confirmation awaited
    EXCHANGE XMITTED : Order sent from Exchange, confirmation awaited
    PENDING : Order confirmed from exchange
    CANCELLED : Order cancelled
    EXECUTED : Order Traded
    GATEWAY REJECT : Order rejected by gateway
    OMS REJECT : Order rejected by oms
    ORDER ERROR : Order rejected from exchange
    FROZEN : Order rejected from exchange (The order will go for a freeze if the quantity is greater than the freeze quantity determined by NSE)
    A.ACCEPT [ADMINACCEPT]
    A.REJECT [ADMINREJECT]
    A.MODIFY [ADMINMODIFY]
    A.CANCEL [ADMINCANCEL]
    AMO SUBMITTED : AMO order submitted successfully
    AMO CANCELLED : AMO order cancelled successfully

Segment Master ID's

    NSE-CASH: 1
    
    NSE-DERIVATIVES: 2
    
    BSE-CASH: 3
    
    BSE-DERIVATIVES: 4
    
    MCX-DERIVATIVES (COMMODITIES): 5
    
    MCX-SPOT (COMMODITIES): 6
    
    NCDEX-DERIVATIVES (COMMODITIES): 7
    
    NCDEX-SPOT (COMMODITIES): 8
    
    NSECDS-DERIVATIVES (CURRENCIES): 13
    
    NSECDS-SPOT (CURRENCIES): 14
```

**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for TradeBook (V2)

```
GET /api/OpenAPI/V2/TradeBook
```

**Operation ID:** `OpenAPIV2_TradeBook`

**Description**

```text
Description

    This API use to get TradeBook of particular Client.

Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
    
Order Status
    
    CLIENT XMITTED : Order sent from client, confirmation awaited
    GATEWAY XMITTED : Order sent from Gateway, confirmation awaited
    OMS XMITTED : Order sent from OMS, confirmation awaited
    EXCHANGE XMITTED : Order sent from Exchange, confirmation awaited
    PENDING : Order confirmed from exchange
    CANCELLED : Order cancelled
    EXECUTED : Order Traded
    GATEWAY REJECT : Order rejected by gateway
    OMS REJECT : Order rejected by oms
    ORDER ERROR : Order rejected from exchange
    FROZEN : Order rejected from exchange (The order will go for a freeze if the quantity is greater than the freeze quantity determined by NSE)
    A.ACCEPT [ADMINACCEPT]
    A.REJECT [ADMINREJECT]
    A.MODIFY [ADMINMODIFY]
    A.CANCEL [ADMINCANCEL]
    AMO SUBMITTED : AMO order submitted successfully
    AMO CANCELLED : AMO order cancelled successfully

Segment Master ID's

    NSE-CASH: 1
    
    NSE-DERIVATIVES: 2
    
    BSE-CASH: 3
    
    BSE-DERIVATIVES: 4
    
    MCX-DERIVATIVES (COMMODITIES): 5
    
    MCX-SPOT (COMMODITIES): 6
    
    NCDEX-DERIVATIVES (COMMODITIES): 7
    
    NCDEX-SPOT (COMMODITIES): 8
    
    NSECDS-DERIVATIVES (CURRENCIES): 13
    
    NSECDS-SPOT (CURRENCIES): 14
```

**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for NetPosition (V2)

```
GET /api/OpenAPI/V2/NetPosition
```

**Operation ID:** `OpenAPIV2_NetPosition`

**Description**

```text
Description

    This API use to get NetPositon of particular Client.

            
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
    
Segment Master ID's

    NSE-CASH: 1
    
    NSE-DERIVATIVES: 2
    
    BSE-CASH: 3
    
    BSE-DERIVATIVES: 4
    
    MCX-DERIVATIVES (COMMODITIES): 5
    
    MCX-SPOT (COMMODITIES): 6
    
    NCDEX-DERIVATIVES (COMMODITIES): 7
    
    NCDEX-SPOT (COMMODITIES): 8
    
    NSECDS-DERIVATIVES (CURRENCIES): 13
    
    NSECDS-SPOT (CURRENCIES): 14
```

**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---
