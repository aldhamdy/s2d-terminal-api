# Control Actions `(ca)`

#### Control action (ca) is parameter returned on every API response.

It's a server instruction that tell the app to execute specific actions in background or to inform the user with an instant event.

> **IF** `(a)` value is `NULL` , `0` or `Empty`, that's mean no action required.

##### List Of Action Control

CA Code | Desc | Action to execute | Notes
---------|----------|---------|
1015 | Log Off the user and delete all session data | Sesstion=>LogOff||
