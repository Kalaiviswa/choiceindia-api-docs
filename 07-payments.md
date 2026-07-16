# Payments

Endpoints for adding funds to the trading account (Net Banking, HDFC UPI, RazorPay), payment acknowledgement, payout and debit funds.

### API for Payment via NetBanking

```
POST /api/OpenAPI/PaymentViaNB
```

**Operation ID:** `OpenAPI_PaymentViaAtomFT`

**Description**

```text
Description

    This API use to initiate Net Banking payment request and to receive Redirection URL to redirect Payment Gateway for further transaction processing.
    This API use both AtomFT and Billdesk Payment gateway
    
Parameters

    Amount: Transaction Amt
    
    BankAccNo: Client Account Number
    
    BankIFSCCode: Bank IFSC Code
    
    ProductType: 1 for Equity and 2 for Commodity
    
    UserVPA: User VPA- UPI Address (Virtual Payment Address)
    
    ReturnUrl: Return URL for Payment Gateway redirection after transaction completion

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

Schema: **`PayinOPIRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Amount` | number (double) | No |  |
| `BankAccNo` | string | No |  |
| `BankIFSCCode` | string | No |  |
| `ReturnUrl` | string | No |  |
| `ProductType` | integer (int32) | No |  |
| `SegmentId` | integer (int32) | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Payment via HDFC UPI

```
POST /api/OpenAPI/PaymentViaHDFCUPI
```

**Operation ID:** `OpenAPI_PaymentViaHDFCUPI`

**Description**

```text
Description

    This API use to initiate HDFC UPI request and receive UPI transaction Collect request Status. Further User will receive payment confirmation on UPI App for further processing.
    
Parameters

    Amount: Transaction Amt
    
    BankAccNo: Client Account Number
    
    BankIFSCCode: Bank IFSC Code
    
    ProductType: 1 for Equity and 2 for Commodity
    
    UserVPA: User VPA- UPI Address (Virtual Payment Address)
		
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

Schema: **`UPIPayinOPIRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Amount` | number (double) | No |  |
| `BankAccNo` | string | No |  |
| `ProductType` | integer (int32) | No |  |
| `SegmentId` | integer (int32) | No |  |
| `UserVPA` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Payment via RazorPay

```
POST /api/OpenAPI/PaymentViaRazorPay
```

**Operation ID:** `OpenAPI_PaymentViaRazorPay`

**Description**

```text
Description

    This API use to initiate RazorPay payment request and to receive RazorPay redirection URL for further transaction processing.
    

Parameters
    
    Amount: Transaction Amt
    
    BankAccNo: Client Account Number
    
    BankIFSCCode: Bank IFSC Code
    
    ProductType: 1 for Equity and 2 for Commodity
    
    PaymentType: 0 for NetBanking and 1 for UPI
    
    UPIId: User VPA (Virtual Payment Address)

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

Schema: **`RazorPayOPIRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Amount` | number (double) | No |  |
| `BankAccNo` | string | No |  |
| `BankIFSCCode` | string | No |  |
| `ProductType` | integer (int32) | No |  |
| `PaymentType` | integer (int32) | No |  |
| `UPIId` | string | No |  |
| `SegmentId` | integer (int32) | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Payment Acknowldgement Response

```
POST /api/OpenAPI/PaymentAckResponse
```

**Operation ID:** `OpenAPI_PaymentAckResponse`

**Description**

```text
Description

    This API use to get Payment Acknowldgement Response for the any transaction initiated.
    
Parameters

    TransactionId: Transaction Id generated by system and received by client while payin request initiate.
		
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
```

**Consumes:** `application/json`, `text/json`, `application/xml`, `text/xml`, `application/x-www-form-urlencoded`  
**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Request Body**

Schema: **`PaymentAckOPIRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `TransactionId` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Process Payout Request

```
POST /api/OpenAPI/ProcessPayout
```

**Operation ID:** `OpenAPI_ProcessPayout`

**Description**

```text
Description

    This API use to initiate Payout request and to receive request Status.
    


Parameters

    ProductType: 1 for Equity, 2 for Commodity
    
		

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

Schema: **`PayoutOPIRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Amount` | number (double) | No |  |
| `ProductType` | integer (int32) | No |  |
| `BankAccNo` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for Debit Funds

```
POST /api/OpenAPI/DebitFunds
```

**Operation ID:** `OpenAPI_DebitFunds`

**Description**

```text
Description

    This API use to initiate Debit Funds request and to receive request Status.
    


Parameters

    Product: Amount for which amount to be blocked
    Amount: Amount to be blocked
		

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

Schema: **`DebitFundsOPIRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Amount` | number (double) | No |  |
| `Product` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---
