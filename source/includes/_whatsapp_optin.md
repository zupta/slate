# Whatsapp opt-out/opt-in API

>__URL__

```
https://www.clickpost.in/api/v1/enable_shipment_notification/?key=<enterprise_key>

Headers: {'Content-type': 'application/json'}
```

>__Request__

```json
{
    "awb":"<awb_number>",
    "whatsapp_disable":true
}
```

>__Response__

```json
{
    "meta": {
        "success": true,
        "status": 200,
        "message": "SUCCESS"
    }
}
```

The whatsapp optin API allows you to inform Clickpost systems if whatsapp communication shall be enabled/disabled for a particular shipment.

The API is a HTTP POST request to:
`https://www.clickpost.in/api/v1/enable_shipment_notification/` 

where output is json

Listed below are the URL parameters:

Parameter | Type | Description
--------- | ---- | -----------
key (required) | character | your Clickpost API Key

Payload

Parameter | Type | Description
--------- | ---- | -----------
awb | character | shipment for which action is to be performed
whatsapp_enable | boolean | action to be done: true implies whatsapp communication shall be sent for the shipment, false implies whatsapp communication shall be disabled


###Response Explanation:

1. "meta" stores information about the API, success or failure
  - success: true/false, true if the API worked fine, else false
  - message: SUCCESS if everything is fine, else the error message 
  - status: 200, if the API data was fine