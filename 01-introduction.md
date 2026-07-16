# Introduction

**API:** OpenAPIInterface_API V1  
**Version:** v1  
**Schemes:** https

> The OpenAPI spec declares an internal host `openapi`. Use the production base URL provided by Choice FinX during onboarding. All endpoint paths in this documentation are relative to that base URL.

# Introduction 
The Open API Interface is a set of HTTP Web APIs that provide Transactional services of basic trading platform for registered entities such as Login & account service, Order, Trade, Margin & Fundsview, Orderbook, Tradebook, Order Trade Messages, Holdings, Net Position, Brodcast data, Payments transfer to trading account, Payout, EDIS facitlity for Non POA Clients and much more. The APIs deals with JSON request and response structures. This document will provide step by step guide to use the API right from Authentication Login to the request response of structure of the API, error codes and messages. 
 # Getting Started
 First of all the client need to register with system then Login with provided credentials using Login API and obtain the Login response including secret Sessionid produced by the System. This SessionId is mandatory to pass in every API (excluding Login,Change,Forgot Password) request Header under Authorization with precision of word 'SessionId'. API will respond with HTTP 401 Unauthorized in case of SessionId expired or doesnt exist else HTTP 200 with success response. Further the document will provide information of all the APIs. 
 # Important Points 
1. VendorId and VendorKey mandatory to pass in request header in keys **VendorId: TEST**, **VendorKey: XXXXXXX** in every request. VendorId and VendorKey will be given in person.
2. All Passwords related fields need to be encrypted with **AES CBC 256 PKCS7 Encoding** Algorithm in request. Encoding Key and IV will be given in person.
3. SessionId mandatory to pass in Authourization request header in every API request apart from Login. More details described in Authentication section below.
# Generate API Key 
1. Log in to the Choice FinX Website.
2. Go to Profile section > Generate API Key.
3. Enter the Vendor Name and select the Validity time.

## Authentication Overview

- **Scheme:** `apiKey` (type `apiKey`)
- **Location:** `header` header named `Authorization`
- Here need to send secret SessionId received in Login response in the format '**SessionId XXXXXXX**' in Authorization request Header in every API request.
