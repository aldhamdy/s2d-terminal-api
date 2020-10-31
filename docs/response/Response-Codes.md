---
tags: [response]
---

# Response Codes (`rc`)

Document to explian the response code of API
<!-- theme: info -->
> ***S2D Platform API had a unified response structure.***


Every API response is a JSON object that has the following items:
```json json_schema
{
  "type": "object",
  "properties": {
    "rc": {
            "type": "string",      
            "description": "Response code"
          },
          "rd": {
            "type": "string",
            "description": "Response description"
          },
          "ca": {
            "type": "number",
            "description": "Control action, sent from server to be executed on terminal."
          },
           "rb": {
            "type": "object",
            "description": "inner response body"
          }
  },
  "required":[
    "rc"
  ]
}
```
#


> **Cesponse code (`rc`)** is the status of the request procesing status.
>if `rc = 0`  that is mean request **Success**, otherwise request **Failed.**
<!-- theme: warning -->
> **Response code**  **`-200`** is a spicial response value indecating that payment request was sent to payment gateway but, server coul'd not get a clear status from gateway, so system decided to hold the transaction and inform user that he/she must check status after some time to get a final status.

> **Control Action `ca`** is action code sent from server to be executed on app, app must check in every response for value of this param and execute the action.

>**Response Body `rb`** is the spicific response body (inner body), and it's optional.
#
### Examples

<!-- type: tab
title: Success Response
-->
```json
{
  "rc" : "0", //success response
  "rd" : "Request processed successfuly",
  "ca" : 0, // o means no action required
  "rb" : // in case there is data returned from server it will be here
  [
    {
      "useCode": 1233,
      "useName": "صلاح محمد احمد",
      "useLogin": "774463333",
      ...

    }
  ]
}
```
<!-- type: tab
title: Failure Response
-->
```json
{
  "rc" : "32", //error 
  "rd" : "User name or password not correct",
  "ca" : 0, // o means no action required
  // rb: null -- if there is no body value , body item will be removed.
}
```
<!-- type: tab-end -->
#

### List Of Response Codes 
These are the reponses needed interaction from developer
<!-- title: List Of Response Codes -->
Code | Desc | Required Action | Notes
---------|----------|---------|------
 0 | Request Success | Inform User with success state||
 -100 | Response was failed due to error in `payment gateway` | inform user that the failuer was from `payment gateway` and display the returned msg to user||
 -200 | Request status is **hold** due to `timeout` or `uncleare response `from payment gateway | inform user with warning status and guid user to check the status of this transaction later||
 -300|Request with the same `ref` from the same user was found with `Success` status |if this is the first try, no action needed. but, if it's retry request then app must consider the status returned with response body||







