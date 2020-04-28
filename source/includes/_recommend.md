# Recommendation API

>URL to hit

```
https://www.clickpost.in/api/v1/recommendation_api/?key=2e9b19ac-8e1f-41ac-a35b-4cd23f41ae17

(key needs to be replaced with the key provided to you)
```

>__Example(POST Body)__

```json
[{
    "pickup_pincode": "110017",
    "drop_pincode": "110019",
    "order_type": "PREPAID",
    "reference_number": "1",
    "item": "bottle",
    "invoice_value": 1245,
    "delivery_type": "FORWARD",
    "weight": 10,
    "height": 10,
    "length": 10,
    "breadth": 10,
    "additional": {
        "custom_fields": [{
            "key": "ptl_or_ftl",
            "value": "PTL"
        }, {
            "key": "truck_size",
            "value": "14 feet"
        }]
    }
}]
```

>__Response__

```json
{
    "result": [
        {
            "form_tax_details": [
                {
                    "entry_tax": false,
                    "form_name": ""
                }
            ],
            "request_details": {
                "order_type": "PREPAID",
                "drop_pincode": "110019",
                "reference_number": "1",
                "delivery_type": "FORWARD",
                "pickup_pincode": "110017",
                "invoice_value": 1245,
                "item": "bottle"
            },
            "preference_array": [
                {
                    "cp_name": "Fedex",
                    "cp_id": 1,
                    "account_code": "Fedex Economy",
                    "priority": 1
                },
                {
                    "cp_name": "Fedex",
                    "cp_id": 1,
                    "account_code": "Fedex Standard Overnight",
                    "priority": 2
                }
            ],
            "pincode_serviceable": true
        }
    ],
    "meta": {
        "message": "SUCCESS",
        "success": true,
        "status": 200
    }
}
```

It’s a POST request as follows

URL:
`https://www.clickpost.in/api/v1/recommendation_api/`

Headers: {'Content-type': 'application/json'}

####URL Parameters:

Parameter | Type | Description
--------- | ---- | -----------
key | character | API key provided to you

####POST Parameters:

Format: JSON

###Compulsory Fields

Payload is a list of json objects each of which have following fields:

Parameter | Type | Description
--------- | ---- | -----------
pickup_pincode | character | pincode of pickup address
drop_pincode | character | pincode of drop address
order_type | character | COD/PREPAID
reference_number | character | to identify each json object uniquely
item | character | item that you wish to send
invoice_value | double | invoice value of the shipment
delivery_type | character | FORWARD/RVP
additional | JSON object | custom parameters in the API request

###Optional Fields

In case you want the recommendation logic to incorporate pricing as a parameter as well please pass the following fields in the API. If not passed, the pricing given by you in the system will not be entertained as a parameter.

Parameter | Type | Description
--------- | ---- | -----------
weight | integer | weight of the shipment
length | integer | length of the shipment
breadth | integer | breadth of the shipment
height | integer | height of the shipment


###Response explanation:

Response object has two parts:

1. meta: stores information about the API, success or failure
    + success: true/false, tells whether the order was created or not
    + message: SUCCESS in case order was created successfully, else returns error message.
    + status:
        1. 200 if the order is created successfully,
        2. 400 if there is a bad request encountered: errors will be present in “message”
2. result: It’s a list of multiple objects, each corresponding to the request json objects, with unique identifier: reference_number. For each json object in result, refer:
    + pincode_serviceable: this field will let you know whether the pincode is serviceable by any courier partner or not. Values: true: if the pincode is serviceable else false
    + preference_array: it’s the list of eligible courier partners for the corresponding reference_number. It has following fields
        1. cp_id: courier partner id as mentioned on page 1 of this document
        2. cp_name: name of the courier partner
        3. account_code: account code created while adding credentials on Clickpost dashboard, this is useful if you have multiple accounts for a courier partner
        3. priority: priority


<aside class="warning">
You must replace key with key provided to you.
</aside>

-------
