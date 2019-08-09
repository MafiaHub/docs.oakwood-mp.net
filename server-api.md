---
description: This page describes the RESTful API for the server.
---

# Server API

{% api-method method="get" host="http://localhost:27010" path="/info" %}
{% api-method-summary %}
Get Server Info
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get server info.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Server info was retrieved.
{% endapi-method-response-example-description %}

```javascript
{  
   "error":false,
   "message":"",
   "servers":[  
      {  
         "name":"Devel Server | TESTERS ONLY",
         "players":0,
         "maxPlayers":128,
         "pass":false,
         "host":"159.89.11.170",
         "port":"8111",
         "version":"b9e44b7f4a662a9a",
         "mapname":"freeride"
      }
   ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



