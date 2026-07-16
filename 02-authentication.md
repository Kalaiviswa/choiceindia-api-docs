# Authentication & Account

This section covers client registration, TOTP-based login, session generation and user profile endpoints. The `SessionId` returned by the login flow must be sent in the `Authorization` header (format: `SessionId XXXXXXX`) on every subsequent request.

### API for Register

```
GET /api/OpenAPI/Register
```

**Operation ID:** `OpenAPI_Register`

**Description**

```text
Description

    This API use to register existing client as OpenAPI user.

            
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
```

**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for LoginTOTP

```
POST /api/OpenAPIV1/LoginTOTP
```

**Operation ID:** `OpenAPI_LoginTOTP`

**Description**

```text
Description

    This API use for login to system and obtain Logon status.
   
Authentication

    VendorId: A unique identifier for the vendor.
    VendorKey: A secret key associated with the vendor.
    Bearer Token: An API token generated after logging into the Finx Website. It must be included in the headers.
    Steps to get the API Key are provided in a separate document.
    
Example Header:

    VendorId: XYZ  
    VendorKey: 0DAZLDQRABCDFERRRRRR2EY7QXC  
    Bearer: Generate API Key
   
Parameters

    MobileNo:Encrypted MobileNo with AES CBC 256 PKCS7 Encoding Algo.

Example Request Body (JSON Format):

{
  "MobileNo": "7jsrik8nFqN9nIbsz2/Iww=="
}
 
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
```

**Consumes:** `application/json`, `text/json`, `application/xml`, `text/xml`, `application/x-www-form-urlencoded`  
**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Request Body**

Schema: **`DocLoginRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `MobileNo` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for ValidateTOTP

```
POST /api/OpenAPIV1/ValidateTOTP
```

**Operation ID:** `OpenAPI_ValidateTOTP`

**Description**

```text
Description

    This API use for login to system via Validating login OTP.
    
Authentication

    VendorId: A unique identifier for the vendor.
    VendorKey: A secret key associated with the vendor.
    Bearer Token: An API token generated after logging into the Finx Website. It must be included in the headers.
    Steps to get the API Key are provided in a separate document.
 
Example Header:

    VendorId: XYZ  
    VendorKey: 0DAZLDQRABCDFERRRRRR2EY7QXC  
    Bearer: Generate API Key

Parameters

    MobileNo: Encrypted MobileNo with AES CBC 256 PKCS7 Encoding Algorithm.
    Otp: Login OTP sent via Email and mobile SMS.

Example Request Body (JSON Format):

{
  "MobileNo": "46c3T067NbcuKQjf+99lSw==",
  "OTP": "122574"
}

Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
```

**Consumes:** `application/json`, `text/json`, `application/xml`, `text/xml`, `application/x-www-form-urlencoded`  
**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Request Body**

Schema: **`DocValidateTOTPRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `MobileNo` | string | No |  |
| `Otp` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for GetClientLoginTOTP

```
POST /api/OpenAPIV1/GetClientLoginTOTP
```

**Operation ID:** `OpenAPI_GetClientLoginTOTP`

**Description**

```text
Description

    This API use to get Login OTP of Client.

            
Authentication

    VendorId: A unique identifier for the vendor.
    VendorKey: A secret key associated with the vendor.
    Bearer Token: An API token generated after logging into the Finx Website. It must be included in the headers.
    Steps to get the API Key are provided in a separate document.
 
Example Header:

    VendorId: XYZ  
    VendorKey: 0DAZLDQRABCDFERRRRRR2EY7QXC  
    Bearer: Generate API Key

Parameters

    MobileNo:Encrypted MobileNo with AES CBC 256 PKCS7 Encoding Algo.
 
Example Request Body (JSON Format):

{
  "MobileNo": "7jsrik8nFqN9nIbsz2/Iww=="
}
            
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
```

**Consumes:** `application/json`, `text/json`, `application/xml`, `text/xml`, `application/x-www-form-urlencoded`  
**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Request Body**

Schema: **`DocGetLoginOTPRequest`**

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `MobileNo` | string | No |  |


**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for UserProfile

```
GET /api/OpenAPI/UserProfile
```

**Operation ID:** `OpenAPI_UserProfile`

**Description**

```text
Description

    This API use to fetch User Profile Details.

    
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
```

**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---

### API for UserProfile

```
GET /api/OpenAPI/UserProfileV2
```

**Operation ID:** `OpenAPI_UserProfile`

**Description**

```text
Description

    This API use to fetch User Profile Details.

    
Parameter Types

    1."string" stands for String Type
    2.0 (Zero) stands for Numeric.
```

**Produces:** `application/json`, `text/json`, `application/xml`, `text/xml`

**Responses**

| Code | Description | Schema |
| --- | --- | --- |
| 200 | Sucess Response | `ResponseMessage` |
| 401 | Unauthorized, Session expired or does'nt exists | `string` |

---
