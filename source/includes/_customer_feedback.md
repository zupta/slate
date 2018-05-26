# Customer Feedback API

>URL to hit

```
https://www.clickpost.in/api/v1/ndr_user_feedback/?username=test&key=42d42a34-ae09-4693-%20b20c-ae2624&start_date=1509529561&end_date=1512121581

(username and key needs to be replaced with the key provided to you)
```

>__Example - GET Request__

```
https://www.clickpost.in/api/v1/ndr_user_feedback/?username=test&key=42d42a34-ae09-4693-%20b20c-ae2624&start_date=1509529561&end_date=1512121581
```

>__Response__

```json
{
    "result": [{
        "phone": null,
        "api_data_push": null,
        "created_at": "2018-05-20T07:44:24.704183Z",
        "type": "CUSTOMER_FEED",
        "landmark": null,
        "comment": "Shipment Delayed",
        "clickpost_status_code": 9,
        "awb": "SF16384627NER",
        "preferred_time": null,
        "preferred_date": null,
        "address": null,
        "clickpost_status_description": "Delivery Failed"
}],
    "meta": {
        "meta": {
            "message": "Success",
            "success": true,
            "status": 200
        }
    }
}
```

This api gives the list of feedback submitted through clickpost tracking page from start date to end date; errors/warnings will be highlighted in the response.

It’s a GET request as follows

URL:
`https://www.clickpost.in//api/v1/ndr_user_feedback/
`

Headers: {'Content-type': 'application/json'}

####URL Parameters:

Parameter | Type | Description
--------- | ---- | -----------
key | character | API key provided to you
username | character | username provided to you

####GET Parameters:

Format: JSON

###Compulsory Fields

Parameter | Type | Description
--------- | ---- | -----------
start_date | long | UTC epoch start time
start_date | long | UTC epoch end time

###Response explanation:

Response object has two parts:

1. meta: stores information about the API, success or failure
    + success: true/false, tells whether the request was processed successfully by Clickpost 
    + message: SUCCESS in case request was successfully processed by Clickpost, else returns error message.
    + status:
        1. 200 if the request is processed successfully,
        2. 400 if there is a bad request encountered: errors will be present in “message”
2. result: 
    + address: New Address change by end user
    + comment: comment/description of change by end user
    + preferred_time: Preferred time of delivery 
    + preferred_date: prefered date of delivery
    + landmark: landmark for the address
    + created_at: timestamp when the user made request for this change
    + awb: awb number for which change is requested
    + phone: new phone number for delivery   
    + clickpost_status_code: shipment status code when customer entered the feedback 
    + clickpost_status_description: shipment status description when customer entered the feedback
    + type: either CLIENT_OPS_FEED or CUSTOMER_FEED
    + api_data_push: if the data is pushed via api to courier company or not, null means we did not try to push, true is successfully pushed and false if failed to push.

<aside class="warning">
You must replace username / key with username / key provided to you.
</aside>

-------