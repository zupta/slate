# Expected Date of Delivery API

>URL to hit

```
https://www.clickpost.in//api/v1/predicted_sla_api/?username=test&key=42d42a34-ae09-4693-%20b20c-ae2624

(username and key needs to be replaced with the key provided to you)
```

>__Example(POST Body with courier partner provided)__

```json
[
    {
        "pickup_pincode": "600040",
        "drop_pincode": "421504",
        "optional" : {
            "cp_id" :5,
            "awb": "ABCD12345"
        }
    }
]
```

>__Response__

```json
{
    "meta": {
        "status": 200,
        "success": true,
        "message": "SUCCESS"
    },
    "result": [
        {
            "predicted_sla_min": 1,
            "min_sla_cp_id": 5,
            "predicted_sla_max": 1,
            "all_map": {
                "5": [
                    1,
                    1
                ]
            }
        }
    ]
}
```

>__Example(POST Body across all courier partners)__

```json
[
    {
        "pickup_pincode": "600040",
        "drop_pincode": "421504"
    }
]
```

>__Response__

```json
{
    "meta": {
        "status": 200,
        "success": true,
        "message": "SUCCESS"
    },
    "result": [
        {
            "predicted_sla_min": 1,
            "min_sla_cp_id": 5,
            "predicted_sla_max": 1,
            "all_map": {
                "3": [
                    2,
                    3
                ],
                "4": [
                    3,
                    6
                ],
                "5": [
                    1,
                    1
                ],
                "6": [
                    1,
                    1
                ],
                "14": [
                    2,
                    3
                ],
                "15": [
                    1,
                    1
                ],
                "1001": [
                    1,
                    1
                ]
            }
        }
    ]
}
```

The expected date of delivery API computes the minimum/maximum time range, a shipment lifecycle may take between the pickup and drop pincode using our predictive machine learning algorithm. By default, it computes the range for all courier companies available and gives the courier partner id which might deliver the shipment fastest. Optional courier comapny id can be passed to see the range for a specific courier partner; errors/warnings will be highlighted in the response.

It’s a POST request as follows

URL:
`https://www.clickpost.in/api/v1/predicted_sla_api/`

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

<!--In case you want the expected date of delivery api to show sla only for given courier company, please pass the following fields in the API. -->

Parameter | Type | Description
--------- | ---- | -----------
cp_id | integer | courier partner id
awb | char | awb for which expected delivery date is to be calculated

List of courier partners is present at:
<a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>


###Response explanation:

Response object has two parts:

1. meta: stores information about the API, success or failure
    + success: true/false, tells whether the request was processed successfully by Clickpost 
    + message: SUCCESS in case request was successfully processed by Clickpost, else returns error message.
    + status:
        1. 200 if the request is processed successfully,
        2. 400 if there is a bad request encountered: errors will be present in “message”
2. result: 
    + predicted_sla_min: minimum sla in days predicted by Clickpost between the given pin codes
    + predicted_sla_max: maximum sla in days predicted by Clickpost between the given pin codes
    + min_sla_cp_id: courier partner id corresponding to the smallest sla of shipment between the pin codes given   
    + all_map: contains [min, max] values for all courier partners serviced by Clickpost


<aside class="warning">
You must replace username / key with username / key provided to you.
</aside>

-------