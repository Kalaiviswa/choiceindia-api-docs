# Orders (V1)  —  *to be deprecated*

> **Note:** These V1 order endpoints are marked for deprecation. Prefer the [Orders (V2)](04-orders-v2.md) endpoints for new integrations.

### API for New order

```
POST /api/OpenAPI/NewOrder
```

**Operation ID:** `OpenAPI_NewOrder`

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
    
    ExchangeOrderNo: for entry = 0, modifiaction and cancellation value received from exchange
    
    RequestType: 1 for entry, 2 for modification,3 for cancellation
    
    GatewayOrderNo: for entry = 0, modifiaction and cancellation value received from exchange
    
    ExchangeOrderTime: for entry = 0, modifiaction and cancellation value received from exchange
    
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

Schema: **`NewOrderRequest`**

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
| `ClientOrderNo` | integer (int32) | No |  |
| `ModeTyp` | string | No |  |
| `Mode` | integer (int32) | No |  |
| `DeviceId` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Modify Order

```
POST /api/OpenAPI/ModifyOrder
```

**Operation ID:** `OpenAPI_ModifyOrder`

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
    
    ExchangeOrderNo: for entry = 0, modifiaction and cancellation value received from exchange
    
    RequestType: 1 for entry, 2 for modification,3 for cancellation
    
    GatewayOrderNo: for entry = 0, modifiaction and cancellation value received from exchange
    
    ExchangeOrderTime: for entry = 0, modifiaction and cancellation value received from exchange
    
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

Schema: **`ModifyOrderRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `ExchangeOrderNo` | string | No |  |
| `GatewayOrderNo` | string | No |  |
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
| `ClientOrderNo` | integer (int32) | No |  |
| `Mode` | integer (int32) | No |  |
| `DeviceId` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Cancel Order

```
POST /api/OpenAPI/CancelOrder
```

**Operation ID:** `OpenAPI_CancelOrder`

**Description**

```text
Description

    This API use to cancel the placed order.

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
    
    ExchangeOrderNo: for entry = 0, modifiaction and cancellation value received from exchange
    
    RequestType: 1 for entry, 2 for modification,3 for cancellation
    
    GatewayOrderNo: for entry = 0, modifiaction and cancellation value received from exchange
    
    ExchangeOrderTime: for entry = 0, modifiaction and cancellation value received from exchange
    
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

Schema: **`CancelOrderRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `ExchangeOrderTime` | string | No |  |
| `ModeTyp` | string | No |  |
| `ExchangeOrderNo` | string | No |  |
| `GatewayOrderNo` | string | No |  |
| `TradedQty` | integer (int32) | No |  |
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
| `ClientOrderNo` | integer (int32) | No |  |
| `Mode` | integer (int32) | No |  |
| `DeviceId` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for OrderBook

```
GET /api/OpenAPI/OrderBook
```

**Operation ID:** `OpenAPI_OrderBook`

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

### API for OrderBookByOrderNo

```
GET /api/OpenAPI/OrderBookByOrderNo/{OrderNo}
```

**Operation ID:** `OpenAPI_OrderBook`

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
| `OrderNo` | path | integer (int32) | Yes |  |

**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for OrderBookV2

```
GET /api/OpenAPI/OrderBookV2
```

**Operation ID:** `OpenAPI_OrderBookV2`

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

### API for TradeBook

```
GET /api/OpenAPI/TradeBook
```

**Operation ID:** `OpenAPI_TradeBook`

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

### API for Holdings

```
GET /api/OpenAPI/Holdings
```

**Operation ID:** `OpenAPI_HoldingsNew`

**Description**

```text
Description

    This API use to get Holdings of particular Client.
            

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

### API for NetPosition

```
GET /api/OpenAPI/NetPosition
```

**Operation ID:** `OpenAPI_NetPosition`

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

### API for OrderTradeMessages

```
POST /api/OpenAPI/OrderMessages
```

**Operation ID:** `OpenAPI_OrderMessages`

**Description**

```text
Description

    This API use to get Order or Trade Messages for the particular Order or  Trade Id.
    
Parameters

    Id: Pass Empty to get all Messages Order and Trades, ExchangeOrderId OR Symbol to get particular Order/Symbol Messages

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

Schema: **`OrderMsgsRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Id` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Position Conversion

```
POST /api/OpenAPI/PositionConversion
```

**Operation ID:** `OpenAPI_PositionConversion`

**Description**

```text
Description

    This API use to convert Positions from Intraday to Delivery and vice versa.
    
Parameters
    
    BUYSELL: 1 For Buy and 2 for Sell
        
    ProductType: for bracket Order this field value will be "D" Delivery/Carryforward only.
        
    SourceProductType: for bracket Order this field value will be "B"
        
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

Schema: **`PositionConversionRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `SegmentId` | integer (int32) | No |  |
| `Token` | integer (int32) | No |  |
| `ClientOrderNo` | integer (int64) | No |  |
| `BuySell` | integer (int32) | No |  |
| `Quantity` | integer (int32) | No |  |
| `ProductType` | string | No |  |
| `SourceProductType` | string | No |  |
| `IsEDISReq` | boolean | No |  |
| `ModeTyp` | string | No |  |
| `Mode` | integer (int32) | No |  |
| `DeviceId` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Order Charges

```
POST /api/OpenAPI/OrderCharges
```

**Operation ID:** `OpenAPI_OrderCharges`

**Description**

```text
Description

    This API use to fetch Order Charges details.

Parameters

    
    BS : 1 for Buy 2 for Sell
    
    ProductType: M for Margin/Intraday, D for Delivery
            
    
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

Schema: **`OrderChargesRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `SegmentId` | integer (int32) | No |  |
| `Token` | integer (int32) | No |  |
| `BS` | integer (int32) | No |  |
| `ProductType` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---
