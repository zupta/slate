# Edit Order API

>URL to hit

```
https://www.clickpost.in/api/v1/edit-order?key=2e9b19ac-8e1f-41ac-a35b-4cd23f41ae17

(key needs to be replaced with the key provided to you)
```

>__Example(POST Body)__

```json
{
    "shipment_details": {
        "order_type": "PREPAID",
        "courier_partner": 4
    },
    "awb_number":"111"
}

```

>__Response__

```json
{
    "meta": {
        "status": 200,
        "message": "Order edited successfully",
        "success": true
    }
}
```

It’s a POST request as follows

URL:
`https://www.clickpost.in/api/v1/edit-order/`

Headers: {'Content-type': 'application/json'}

####URL Parameters:

Parameter | Type | Description
--------- | ---- | -----------
key | character | API key provided to you

####POST Parameters:

Format: JSON

####Compulsory Fields

Payload is a list of json objects each of which have following fields:

Parameter | Type | Description
--------- | ---- | -----------
awb | character | awb number

####Optional Fields

Edit Order API currently only supports payment_mode update which is provided in shipment_details object.

Parameter | Type | Description
--------- | ---- | -----------
shipment_details | object | item details


####Response explaination:

Response object has two parts:

1. meta: stores information about the API, success or failure
    + success: true/false, tells whether the order was created or not
    + message: SUCCESS in case order was edited successfully, else returns error message.
    + status:
        1. 200 if the order is created successfully,
        2. 400 if there is a bad request encountered: errors will be present in “message”


<aside class="warning">
You must replace key with key provided to you.
</aside>

####Note

This api is currently being used by 3 courier partners only.

   S.No. | Courier Partner 
--------- | ---- 
1 | Delhivery
2 | EcomExpress
3 | Shadowfox
   
-------
