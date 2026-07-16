# Market Data

Scrip/touchline information, market status and historical chart data.

### API for MultipleTouchlineData

```
POST /api/OpenAPI/MultipleTouchline
```

**Operation ID:** `OpenAPI_MultipleTouchline`

**Description**

```text
Description

    This API use to get MultipleTouchline data or Brodcast data of single or multiple Segment token. This API let you to send multiple or single Segment Token string joined with '@' separated with ','.
    MultipleSegToken: SegmentId@Token comma separated
    

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

Schema: **`MultipleTouchlineRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `MultipleSegToken` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Scrip Details

```
POST /api/OpenAPI/ScripDetails
```

**Operation ID:** `OpenAPI_ScripDetails`

**Description**

```text
Description

    This API use to fetch Scrip details.

Parameters

    
    SegmentId : SegmentId (Exchange Id)
    
    Token: Scrip Token
            
    
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

Schema: **`ScripDetailsRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `SegmentId` | integer (int32) | No |  |
| `Token` | integer (int32) | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for MarketStatus

```
GET /api/OpenAPI/MarketStatus
```

**Operation ID:** `OpenAPI_MarketStatus`

**Description**

```text
Description

    This API use to get Market Status details.
    
    

Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
    
Response

    Status:
        0 - Preopen
        1 – Open
        2 – Close
        3 - Preopen End
        20 – Matching Open
        21 – Matching Close
        Matching Open/Close is applicable for BSE SPOS/PCS Session

    MarketType:
        1 - Normal
        2 - OddLot
        3- Spot
        7- After Market Open AMO
        8 - Extended Session
    
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

### API for Graph Data History

```
POST /api/OpenGraph/ChartData
```

**Operation ID:** `OpenAPI_GetChartData`

**Description**

```text
Description

    This API Returns Historical Graph data (EOD or Intraday) for given duration between from, to date and Interval		
    
Parameters

    FromDate :      
    Epoch time in terms of Total Seconds from 1980-01-01
    Eg- FromDate is 01 May 2021 then need to calculate total seconds from 01 Jan 1980 to 01 May 2021
    
    ToDate :      
    Epoch time in terms of Total Seconds from 1980-01-01	
    Eg- FromDate is 02 May 2021 then need to calculate total seconds from 01 Jan 1980 to 02 May 2021
            
    Interval : 
    For EOD timeframe:
        'D' for Daily          
        'W' for Weekly
        'M' for Monthly        
        'Q' for Quarterly
        'H' for HalfYearly     
        'Y' for Yearly
        'T' for ThreeYearly    
        'F' for FiveYearly
            
    For Intraday timeframe   
        '1' for 1 Minute       
        '5' for 5 Minute		
        '10' for 10 Minute
        '15' for 15 Minute
        '30' for 30 Minute (Half hour)		    
        '60' for 60 Minute (Hour)
		
Important Instructions 
    
    All Price related fileds are in Paise. User can convert it to Rupee using Price Divisor coming in response
    
    All datetime values are in terms of total seconds from 01-01-1980. User need to convert it from seconds to datetime
    
    All price data points are corporate action adjusted data

Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
            
Segment Master ID's

    NSE-CASH: 1
    
    NSE-DERIVATIVES: 2
    
    BSE-CASH: 3
    
    BSE-DERIVATIVES: 4
    
    MCX-DERIVATIVES (COMMODITIES): 5
    
    NCDEX-DERIVATIVES (COMMODITIES): 7
    
    NSECDS-DERIVATIVES (CURRENCIES): 13
    
Response Parameters

    Change:
    Price Change
    
    PriceDivisor:
    Value to convert price related values from paise to rupee and vice versa
    
    Volume:
    Total Volume traded
    
    lstChartHistory:
    List of below values consolidated order wise
    PriceDate (Datetime in terms of total seconds from 01-01-1980), OpenPrice, HighPrice, LowPrice, ClosePrice, VolumeTraded, OpenInterest
```

**Consumes:** `application/json`, `text/json`, `application/xml`, `text/xml`, `application/x-www-form-urlencoded`  
**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Request Body**

Schema: **`ChartOPIRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `SegmentId` | integer (int32) | No |  |
| `Token` | integer (int32) | No |  |
| `FromDate` | integer (int32) | No |  |
| `ToDate` | integer (int32) | No |  |
| `Interval` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Returns Success Response | `object` |
| 401 | Unauthorized |  |
| 429 | Too Many Requests |  |

---
