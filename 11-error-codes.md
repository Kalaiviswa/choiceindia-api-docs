# Response & Error Codes

Every API returns a common `ResponseMessage` envelope. HTTP `401` indicates an expired or missing session.

## `ResponseMessage` envelope

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `Status` | string | No |  |
| `Response` | object | No |  |
| `Reason` | string | No |  |


## Common HTTP status codes

| Code | Meaning |
| --- | --- |
| 200 | Success response |
| 401 | Unauthorized — session expired or does not exist |
