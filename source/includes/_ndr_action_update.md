# NDR Action Update API

>URL to hit

```
https://www.clickpost.in/api/v1/ndr/update/?username=test&key=42d42a34-ae09-4693-%20b20c-ae2624&cp_id=4

(username and key needs to be replaced with the key provided to you)
```

>__Example - POST Request__

```json
[       
        {
            "waybill": "1823821",
            "act": "DEFER_DLV",
            "action_data": {
                "deferred_date": "2017-12-28"
            }
        },
            {
                "waybill": "3278213",
                "act": "EDIT_DETAILS",
                "action_data": {
                    "name": "name1",
                    "add": "add1",
                    "phone": "2132341412"
                }
            },
            {
                "waybill": "278382",
                "act": "RE-ATTEMPT"
            },
            {
                "waybill": "1278728",
                "act": "INITIATE_RTO"
            }
        ]
```

>__Response__

```json
{
    "result": {
        "ndr_update_status": [
            {
                "cp_response": "UPL15970567163944112616",
                "status": true,
                "awb": "1823821"
            },
            {
                "cp_response": "UPL15970567163944112616",
                "status": true,
                "awb": "3278213"
            },
            {
                "cp_response": "UPL15970567163944112616",
                "status": true,
                "awb": "278382"
            },
            {
                "cp_response": "in valid awb and action not supported",
                "status": false,
                "awb": "1278728"
            }
        ]
    },
    "meta": {
        "message": "Success",
        "success": true,
        "status": 200
    }
}
```

This api instructs the courier company to take action on a awb. Only Four actions supported (DEFER_DLV, EDIT_DETAILS, RE-ATTEMPT, INITIATE_RTO); errors/warnings will be highlighted in the response.

It’s a POST request as follows

Headers: {'Content-type': 'application/json'}

####URL Parameters:

Parameter | Type | Description
--------- | ---- | -----------
key | character | API key provided to you
username | character | username provided to you
cp_id | integer | courier company id provided by clickpost

List of courier partners is present at:
<a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>

####POST Parameters:

Format: JSON

###Compulsory Fields

Parameter | Type | Description
--------- | ---- | -----------
waybill | stiring | awb number for ndr action update
act | long | action to take (DEFER_DLV, EDIT_DETAILS, RE-ATTEMPT)

###Optional Fields

<!--For every action, need different kind of data -->

Parameter | Type | Description
--------- | ---- | -----------
action_data->deferred_date | character | [DEFER_DLV] Deferred date for reattempt in (YYYY-MM-DD) format
action_data->name | character | [EDIT_DETAILS] Name of person to handover the shipment
action_data->add | character | [EDIT_DETAILS] Address where shipment need to be delivered
action_data->phone | character | [RE-ATTEMPT] Phone no of the persion to contact for delivery
NO_DATA | NO_DATA | [RE-ATTEMPT and INITIATE_RTO] No extra data is required

###Response explanation:

Response object has two parts:

1. meta: stores information about the API, success or failure
    + success: true/false, tells whether the request was processed successfully by Clickpost 
    + message: SUCCESS in case request was successfully processed by Clickpost, else returns error message.
    + status:
        1. 200 if the request is processed successfully,
        2. 400 if there is a bad request encountered: errors will be present in “message”
2. result: 
    + ndr_update_status: contains array of ndr update responses for each awb number
    + ndr_update_status->cp_response: courier company reference number for the action requested    
    + ndr_update_status->status: true/false based on if ndr action is updated or not
    + ndr_update_status->awb: awb number corresponding to ndr update action    

<aside class="warning">
You must replace username / key with username / key provided to you.
</aside>

-------