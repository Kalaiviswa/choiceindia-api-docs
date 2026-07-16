# Appendix: Schema Definitions

All request/response object schemas referenced across the API.

## `CancelOrderRequest`

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


## `CancelOrderRequestV2`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `ClientOrderNo` | string | No |  |
| `SegmentId` | integer (int32) | No |  |
| `ModeTyp` | string | No |  |
| `Mode` | integer (int32) | No |  |
| `DeviceId` | string | No |  |


## `ChartOPIRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `SegmentId` | integer (int32) | No |  |
| `Token` | integer (int32) | No |  |
| `FromDate` | integer (int32) | No |  |
| `ToDate` | integer (int32) | No |  |
| `Interval` | string | No |  |


## `DISStatusOPIReq`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `ReqId` | string | No |  |


## `DebitFundsOPIRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Amount` | number (double) | No |  |
| `Product` | string | No |  |


## `DocGetLoginOTPRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `MobileNo` | string | No |  |


## `DocLoginRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `MobileNo` | string | No |  |


## `DocValidateTOTPRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `MobileNo` | string | No |  |
| `Otp` | string | No |  |


## `EDISStock`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `ISIN` | string | No |  |
| `Quantity` | integer (int32) | No |  |


## `MarginReq`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `SegmentId` | integer (int32) | No |  |
| `Token_Qty` | string | No |  |
| `Mode` | integer (int32) | No |  |
| `DeviceId` | string | No |  |


## `ModifyOrderRequest`

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


## `ModifyOrderRequestV2`

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


## `MultipleTouchlineRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `MultipleSegToken` | string | No |  |


## `NewOrderRequest`

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


## `NewOrderRequestV2`

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


## `OrderChargesRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `SegmentId` | integer (int32) | No |  |
| `Token` | integer (int32) | No |  |
| `BS` | integer (int32) | No |  |
| `ProductType` | string | No |  |


## `OrderMsgsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Id` | string | No |  |


## `PayinOPIRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Amount` | number (double) | No |  |
| `BankAccNo` | string | No |  |
| `BankIFSCCode` | string | No |  |
| `ReturnUrl` | string | No |  |
| `ProductType` | integer (int32) | No |  |
| `SegmentId` | integer (int32) | No |  |


## `PaymentAckOPIRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `TransactionId` | string | No |  |


## `PayoutOPIRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Amount` | number (double) | No |  |
| `ProductType` | integer (int32) | No |  |
| `BankAccNo` | string | No |  |


## `PositionConversionRequest`

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


## `RazorPayOPIRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Amount` | number (double) | No |  |
| `BankAccNo` | string | No |  |
| `BankIFSCCode` | string | No |  |
| `ProductType` | integer (int32) | No |  |
| `PaymentType` | integer (int32) | No |  |
| `UPIId` | string | No |  |
| `SegmentId` | integer (int32) | No |  |


## `ResponseMessage`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Status` | string | No |  |
| `Response` | object | No |  |
| `Reason` | string | No |  |


## `ScripDetailsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `SegmentId` | integer (int32) | No |  |
| `Token` | integer (int32) | No |  |


## `UPIPayinOPIRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Amount` | number (double) | No |  |
| `BankAccNo` | string | No |  |
| `ProductType` | integer (int32) | No |  |
| `SegmentId` | integer (int32) | No |  |
| `UserVPA` | string | No |  |


## `VerifyDISOPIReq`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `BOID` | string | No |  |
| `CtrBOID` | string | No |  |
| `ExId` | integer (int32) | No |  |
| `channel` | integer (int32) | No |  |
| `eDISStocks` | array of `EDISStock` | No |  |

**`EDISStock`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `ISIN` | string | No |  |
| `Quantity` | integer (int32) | No |  |

