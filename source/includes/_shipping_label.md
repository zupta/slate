# Generate a shipping label for the order. Remember if the label is already given while creating the manifestation it will give the older shipping label only. To generate the new one please pass regenerate=true in the app.

##Generate a shipping label for an AWB

>GET request. URL:

```
https://www.clickpost.in/api/v1/fetch/shippinglabel/?waybill={waybill_number}&regenerate=False&key={--key given to client--}
Headers: {'Content-type': 'application/json'}
```

>__Sample Payload__
```
Just pass the awb_number in the request param and regenerate True or False
```

>__Response__

```json
{
    "meta": {
        "success": true,
        "status": 200,
        "message": "SUCCESS"
    },
    "result": {
        "shipping_label": "a url having the pdf of the shipping label"
    }
}
```

###Fields Explanation

####Compulsory:

Parameter | Type | Description
--------- | ---- | -----------
key (required) | character | this is the API Key
waybill (required) | character | this is/are comma separated waybill numbers for which the status is required

####Optional:
regenerate (required) | boolean | true or false based on if you want to regenrate label or want the same which was given in manifestation

###Response Explanation:

1. "meta" stores information about the API, success or failure
  - success: true/false, true if the API worked fine, else false
  - message: SUCCESS if everything is fine, else the error message c. status: 200, if the API data was fine, 400 in case of a bad request
2. "result": contains shipping_label pdf for the waybill given in request param       
------
