# Pincode Serviceability API

>URL to hit

```
https://www.clickpost.in/api/v1/serviceability_api/?username=test&key=42d42a34-ae09-4693-%20b20c-ae2624

(username and key needs to be replaced with the key provided to you)
```

>__Example(POST Body)__

```json
[
    {
        "pickup_pincode": "110017",
        "drop_pincode": "110019",
        "optional": {
            "breadth": 10,
            "height": 10,
            "length": 10,
            "weight": 10,
            "invoice_value": 1245,
            "cp_id": 1
        }
    }
]
```

>__Response__

```json
{
    "meta": {
        "success": true,
        "status": 200,
        "message": "SUCCESS"
    },
    "result": [
        {
            "serviceable": {
                "PREPAID": true,
                "COD": true
            },
            "comitted_sla": 3
        }
    ]
}
```

Serviceability api checks if pickup and drop pincodes are serviceabile or not. It accepts the shipment dimension fields as additional parameters. Courier company id can be passed to check the serviceability for a specific courier company.

It’s a POST request as follows

URL:
`https://www.clickpost.in/api/v1/serviceability_api/``

Headers: {'Content-type': 'application/json'}

####URL Parameters:

Parameter | Type | Description
--------- | ---- | -----------
key | character | API key provided to you
username | character | username provided to you

####POST Parameters:

Format: JSON

###Compulsory Fields

Payload is a list of json objects each of which have following fields:

Parameter | Type | Description
--------- | ---- | -----------
pickup_pincode | integer | pincode of pickup address
drop_pincode | integer | pincode of drop address

###Optional Fields

<!--In case you want the serviceability logic to show pricing as a parameter as well, please pass the following fields in the API. -->

Parameter | Type | Description
--------- | ---- | -----------
invoice_value | double | invoice value of the shipment
order_type | character | COD/PREPAID
weight | integer | weight of the shipment
length | integer | length of the shipment
breadth | integer | breadth of the shipment
height | integer | height of the shipment
cp_id | integer | clickpost courier comapny id

###Response explanation:

Response object has two parts:

1. meta: stores information about the API, success or failure
    + success: true/false, tells whether the order was created or not
    + message: SUCCESS in case request was successfully processed by clickpost, else returns error message.
    + status:
        1. 200 if the order is created successfully,
        2. 400 if there is a bad request encountered: errors will be present in “message”
2. result: 
    + serviceable: JSON object which stores following two fields:
    	+ COD: Values: true: if the pincode is COD serviceable else false
    	+ PREPAID: Values: true: if the pincode is COD serviceable else false
    + commited_sla: average commited SLA by courier partner (based on your contract with courier partner) for the shipment if dispatched today. (integer field)


<aside class="warning">
You must replace username / key with username / key provided to you.
</aside>

-------
