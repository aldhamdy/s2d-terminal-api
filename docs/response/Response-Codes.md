---
tags: [response]
---

# Response Codes

S2D Platform Api had a strict response structuer, Every api response has the pattern of :
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
> **Cesponse code `rc`** is the status of the request procesing status.
>
if `rc = 0`  that is mean request **success**, otherwise request **failed**

> **Control Action `ca`** is action code sent from server to be executed on app, app must check in every response for value of this param and execute the action.

>**Response Body `rb`** is the spicific response body (inner body), and it's optional.

###  Response Codes List

Code | Desc | Column C
---------|----------|---------
 A1 | B1 | C1
 A2 | B2 | C2
 A3 | B3 | C3