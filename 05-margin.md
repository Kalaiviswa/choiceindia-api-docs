# Margin

### API for Margin

```
POST /api/OpenAPI/GetMargin
```

**Operation ID:** `Margin_CalcuateMargin`

**Description**

```text
Description

    API for Margin calculation
    Token_Qty: Pass Pipe separated Token and QTY ex: 48552|425
                For Multiple contracts pass Tilde (~) separated Token_Qty ex: 48552|425~48553|500
    
Parameters

 
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
```

**Consumes:** `application/json`, `text/json`, `application/xml`, `text/xml`, `application/x-www-form-urlencoded`  
**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Request Body**

Schema: **`MarginReq`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `SegmentId` | integer (int32) | No |  |
| `Token_Qty` | string | No |  |
| `Mode` | integer (int32) | No |  |
| `DeviceId` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---
