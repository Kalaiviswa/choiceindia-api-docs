# Funds

### API for FundsView

```
GET /api/OpenAPI/FundsView
```

**Operation ID:** `OpenAPI_FundsView`

**Description**

```text
Description

    This API use to get FundsView details or Margin details of particular Client.

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

### API for FundsViewNew

```
GET /api/OpenAPI/FundsViewNew
```

**Operation ID:** `OpenAPI_FundsViewNew`

**Description**

```text
Description

    This API use to get FundsViewNew details or Margin details of particular Client.

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
