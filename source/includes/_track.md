# Track Order

##Register an AWB for tracking

>POST request. URL:

```
https://www.clickpost.in/api/v2/tracking/awb-register/
Headers: {'Content-type': 'application/json'}
```

>__Sample Payload__

```json
{
  "waybill": "ABCDRESDEFGHIJKL1257679",
  "cp_id": 1,
  "key": "42d42a34-ae09-4693-b20c-ae2624218a329",
  "account_code": "Fedex Domestic",
  
  "consumer_details": {
          "name": "Test Customer",
          "phone": "8080808080",
          "email": "test@clickpost.in"
  },
  "shipment_info": {
          "item": "Shirt",
          "order_type": "COD",
          "invoice_value": 1000,
          "reference_number": "123XYZ",
          "length": 10,
          "height": 10,
          "weight": 10,
          "breadth": 10,
          "drop_pincode": "110001",
          "pickup_pincode": "110001",
          "delivery_type": "FORWARD",
          "cod_amount": 1000.10,
          "drop_address": "Roots hacker Home, R 28, Second Floor, Nehru Enclace, Opposite Nehru Place, New Delhi 110001",
          "additional": {
                    "items": [
                        {
                            "sku": "XYZ1",
                            "description": "item1",
                            "quantity": 1,
                            "price": 200,
                            "images": "<Image URL>",
                            "return_days": 2,
                            "additional": {
                                "length": 10,
                                "height": 10,
                                "breadth": 10,
                                "weight": 100
                            }
                        }
                    ]
                  }
  },
  "additional": {
    "order_date": "2017-02-14T18:00:00+05:30",
    "ship_date": "2017-02-14T23:00:00+05:30"
  }
}

```
>__Response__

```json
{
  "meta": {
    "message": "SUCCESS",
    "status": 200,
    "success": true
  },
  "result": {
    "security_key": "530470b0-8ebd-40c3-9c9e-6ca6bf1d29b8",
    "consumer_details": {
      "id": 1
    },
    "shipment_info": {
      "id": 1
    },
    "tracking_id": 1188264
  }
}
```

Note: All orders are passed a security_key in response. Please store this security key to be used in Customer engagement platform.

###Fields Explanation

####Compulsory:

Parameter | Type | Description
--------- | ---- | -----------
key (required) | character | this is the API Key
waybill (required) | character | this is/are comma separated waybill numbers for which the status is required
cp_id (required) | integer | courier_partner_id as specified on page 1 of this documentation
account_code (optional) | string | account code in case you have multiple accounts for same courier partner

####Optional:

####consumer_details (optional): In case you want Clickpost to send notifications to your customers via mail / sms, please pass information in this object:
Parameter | Type | Description
--------- | ---- | ----------- 
name | character (250 chars) | end customer name, who will receive the shipment, this will be used to personalize the SMS / email sent to the customer
phone_number | 10/11 characters | customer phone number on which SMS is to be sent.
email | character (150 chars) | Email address of the customer, on which email is to be sent.

####shipment_info (optional): shipment information for rich analytics on your data:
Parameter | Type | Description
--------- | ---- | ----------- 
item | character (500 chars) | name of item sent to the customer
order_type | character | either COD or PREPAID
invoice_value | float | shipment invoice value
reference_number | character (len: 100) | order_id or reference number to be shared with end customer
length | integer | in cm
breadth | integer | in cm
height | integer | in cm
weight | integer | in grams
drop_pincode | character | 6 digit pincode of drop location
pickup_pincode | character | 6 digit pincode of pickup location
delivery_type | character | either FORWARD / RVP
cod_amount| float field | COD value to be collected from customer, float field
drop_address| character (500 chars) | drop address of the shipment
additional | object | optional field which can have additional information related to items like sku, description, quantity, image, price and return_days for return management solution (easier for end customer to select which product to return)
additional --> items --> return_days | integer | number of days allowed for a product to be accepted as return

####additional (optional): extra information about shipment used to power tracking page:
Parameter | Type | Description
--------- | ---- | ----------- 
order_date | character | timestamp when the order was placed
ship_date | character | timestamp when order was ready to ship

## Un-Track an Order or Mark a shipment expired

You have to be registered for tracking service to use this api, if you have not, please check Registering for Tracking Service Section.

>POST request. URL:

```
https://www.clickpost.in/api/v1/tracking/awb-unregister/
Headers: {'Content-type': 'application/json'}
```

>__Sample Payload__

```json
{
    "cp_id": 1,
    "waybill": "786000454820",
    "key": "8341db95-a25d-4825-9b83-c62c20284b21"
}

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
        "awb": "786000454820"
    }
}
```

###Fields Explanation

####Compulsory:

Parameter | Type | Description
--------- | ---- | -----------
key (required) | character | this is the API Key
waybill (required) | character | this is/are comma separated waybill numbers for which the status is required
cp_id (required) | integer | courier_partner_id [List of courier partners is present at:
<a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>]

###Response Explanation:

1. "meta" stores information about the API, success or failure
  - success: true/false, true if the API worked fine, else false
  - message: SUCCESS if everything is fine, else the error message c. status: 200, if the API data was fine, 400 in case of a bad request
2. "result" is an array of records. Each record holds information of comma-separated waybill entered in the request parameter.        


##Fetch updated-orders list
>__URL__

```
https://www.clickpost.in/api/v1/updated-order?username=<clickpost-username>&key=<clickpost-api-key>&start_date=1531980785&end_date=1531984399

Headers: {'Content-type': 'application/json'}
```

>__Response__

```json
{
    "result": [
        {
            "created_at": "2019-04-15T14:52:45.304018Z",
            "timestamp": "2019-04-15 20:22:43",
            "clickpost_status_description": "OrderPlaced",
            "clickpost_status_code": 1,
            "courier_partner": 9,
            "waybill": "SF41917204SCR",
            "updated_at": "2019-04-15T15:00:04.672388Z"
        },
        {
            "created_at": "2019-04-15T14:47:26.614788Z",
            "timestamp": "2019-04-15 20:17:25",
            "clickpost_status_description": "OrderPlaced",
            "clickpost_status_code": 1,
            "courier_partner": 9,
            "waybill": "SF41917199SCR",
            "updated_at": "2019-04-15T15:00:07.132808Z"
        },
        {
            "created_at": "2019-04-15T13:58:34.822899Z",
            "timestamp": "2019-04-15 19:28:33",
            "clickpost_status_description": "OrderPlaced",
            "clickpost_status_code": 1,
            "courier_partner": 9,
            "waybill": "SF41917168SCR",
            "updated_at": "2019-04-15T15:00:42.625536Z"
        }
    ],
    "meta": {
        "message": "SUCCESS",
        "status": 200,
        "success": true
    }
}
```

The updated-order API retrieves the shipments which are updated between specified start and end time.

The API is a HTTP GET request to:
`https://www.clickpost.in/api/v1/updated-order` 

where output is json

Listed below are the parameters:

Parameter | Type | Description
--------- | ---- | -----------
key (required) | character | this is the API Key
username (required) | character | user name, provided to you
start_date (required) | integer | start time for the query to run. To be passed in epoch time
end_date (required) | integer | end time for the query to run. To be passed in epoch time

Note: The difference between start_date and end_date cannot be more than 30 minutes. If you plan to use polling, Its highly recommended to 1st run updated-order API, get list of updated shipments and then request the status details if required for those shipments using polling.

###Response Explanation:

1. “meta” stores information about the API, success or failure
  - success: true/false, true if the API worked fine, else false
  - message: SUCCESS if everything is fine, else the error message c. status: 200, if the API data was fine, 400 in case of a bad request
2. “result” is an array of records. Each record holds information of comma-separated waybill entered in the request parameter.


##Tracking AWB Using Polling

>__URL__

```
https://www.clickpost.in/api/v2/track-order/?username=testuser&key=2e9b19ac-8e1f- 41ac-a35b-4cd23f41ae17&waybill=3515341&cp_id=10

Headers: {'Content-type': 'application/json'}
```

>__Response__

```json
{
    "meta": {
        "message": "SUCCESS",
        "status": 200,
        "success": true
    },
    "result": {
        "SF18399217NER": {
            "latest_status": {
                "clickpost_status_description": "Delivered",
                "clickpost_status_code": 8,
                "clickpost_status_bucket": 6,
                "status": "Delivered successfully",
                "location": "",
                "remark": "Delivered successfully",
                "timestamp": "2018-07-07 19:34:46"
            },
            "additional": {
                "is_stuck": false,
                "dest_hub_inscan": false,
                "order_detail": [],
                "edd": {
                    "min_sla": 2,
                    "max_sla": 5
                }
            },
            "scans": [
                {
                    "clickpost_status_description": "Delivered",
                    "clickpost_status_code": 8,
                    "clickpost_status_bucket": 6,
                    "status": "Delivered successfully",
                    "location": "",
                    "remark": "Delivered successfully",
                    "tracking_id": 12087859,
                    "timestamp": "2018-07-07 19:34:46",
                    "checkpoint_id": 163921399
                },
                {
                    "clickpost_status_description": "OutForDelivery",
                    "clickpost_status_code": 6,
                    "clickpost_status_bucket": 4,
                    "status": "Out for Delivery",
                    "location": "",
                    "remark": "Out for Delivery",
                    "tracking_id": 12087859,
                    "timestamp": "2018-07-07 08:53:01",
                    "checkpoint_id": 163496669
                },
                {
                    "clickpost_status_description": "InTransit",
                    "clickpost_status_code": 5,
                    "clickpost_status_bucket": 3,
                    "status": "Assigned to a Shadowfax Rider",
                    "location": "",
                    "remark": "Assigned to a Shadowfax Rider",
                    "tracking_id": 12087859,
                    "timestamp": "2018-07-07 08:52:51",
                    "checkpoint_id": 163496670
                },
                {
                    "clickpost_status_description": "InTransit",
                    "clickpost_status_code": 5,
                    "clickpost_status_bucket": 3,
                    "status": "Reached the nearest hub",
                    "location": "",
                    "remark": "Reached the nearest hub",
                    "tracking_id": 12087859,
                    "timestamp": "2018-07-07 08:02:08",
                    "checkpoint_id": 163496671
                },
                {
                    "clickpost_status_description": "OrderPlaced",
                    "clickpost_status_code": 1,
                    "clickpost_status_bucket": 1,
                    "status": "In Manifest",
                    "location": "GUNJAN ",
                    "remark": "In Manifest",
                    "tracking_id": 12087859,
                    "timestamp": "2018-07-07 02:47:21",
                    "checkpoint_id": 163419110
                },
                {
                    "clickpost_status_description": "InTransit",
                    "clickpost_status_code": 5,
                    "clickpost_status_bucket": 3,
                    "status": "Collected by Shadowfax",
                    "location": "GUNJAN ",
                    "remark": "Collected by Shadowfax",
                    "tracking_id": 12087859,
                    "timestamp": "2018-07-07 02:25:34",
                    "checkpoint_id": 163419111
                },
                {
                    "clickpost_status_description": "OrderPlaced",
                    "clickpost_status_code": 1,
                    "clickpost_status_bucket": 1,
                    "status": "Assigned to Shadowfax",
                    "location": "",
                    "remark": "Assigned to Shadowfax",
                    "tracking_id": 12087859,
                    "timestamp": "2018-07-06 05:41:13",
                    "checkpoint_id": 162947643
                }
            ],
            "valid": true
        }
    }
}
```

The track-order API retrieves the historic statuses and the current status of the package.

The API is a HTTP GET request to:
`https://www.clickpost.in/api/v2/track-order/` 

where output is json

Listed below are the parameters:

Parameter | Type | Description
--------- | ---- | -----------
key (required) | character | this is the API Key
username (required) | character | user name, provided to you
waybill (required) | character | this is/are comma separated waybill numbers for which the status is required
cp_id (required) | integer | courier_partner_id as specified on page 1 of this documentation


###Response Explanation:

1. “meta” stores information about the API, success or failure
  - success: true/false, true if the API worked fine, else false
  - message: SUCCESS if everything is fine, else the error message c. status: 200, if the API data was fine, 400 in case of a bad request
2. “result” is an array of records. Each record holds information of comma-separated waybill entered in the request parameter.
3. Each record has following objects:
  - “valid”: (true / false) in case a wrong AWB / AWB which is not yet registered on Clickpost; is entered to track a shipment, “valid” field will be false. If the AWB is correct, “valid” will be true
  - “waybill”: AWB provided in the API. Is the key of each object. The value is a dictionary storing information about shipment:
        1. scans: Stores all scans that happened for shipment. Has following keys:
            + status: status of the shipment at that time
            + remarks: remark given by courier partner
        3. location: location of shipment at the time of the scan
        4. timestamp: date/time in ISO format when the scan was done
        5. clickpost_status_code: clickpost generated status code for particular
        status. Clickpost has mapped various statuses of different courier companies into few status codes, which helps customers understand and take action on statuses in preemptive manner. (Explained on last page of this document)
        6. clickpost_status_description: description of clickpost_status_code (Specified on last page of this document)
  - lateststatus: Stores information about the latest status of shipment, has following fields:
        1. status: status of the shipment at that time
        2. remarks: remark given by courier partner
        3. location: location of shipment at the time of the scan
        4. timestamp: date/time in ISO format when the scan was done
        5. clickpost_status_code: clickpost generated status code for particular
        status. Clickpost has mapped various statuses of different courier companies into few status codes, which helps customers understand and take action on statuses in preemptive manner (Explained on last page of this document)
        6. clickpost_status_description: description of clickpost_status_code (Specified on last page of this document)
        7. clickpost_status_bucket: this is a consolidated id built on top of clickpost_status_codes, that can be used to show status to the customer on your track orders page. It has following distinct values:

clickpost_status_bucket | Meaning | clickpost_status_code clubbed in the bucket
--------- | ---- | -----------
1 | Order Placed by Customer | [1, 2, 3, 28, 25, 10]
2 | Dispatched | [4]
3 | In Transit | [5, 18, 19, 20]
4 | Out For Delivery | [6]
5 | Failed Delivery | [7, 9]
6 | Delivered | [8] 
7 | Returned: When shipment is in return journey due to customer rejection | [11, 12, 13, 14, 15, 21, 26, 27]
8 | Lost | [16]
9 | Damaged | [17]


6, 7, 8: These are terminal buckets in shipment journey


##Tracking AWB Using Webhooks

>__Webhook Payload Header__

```json
{
  "Content-Type": "application/json",
  "webhook_key": "webhook_key_given_during_webhooks_register"
}
```

>__Webhook Payload__

```json

{
  "waybill": "P0109276342",
  "clickpost_status_code": 6,
  "cp_id": 14,
  "clickpost_status_description": "OutForDelivery",
  "status": "O",
  "location": "VASAI, MUMBAI",
  "timestamp": "2017-08-02T13:23:02Z",
  "remark": "Out For Delivery",
  "additional": {
    "latest_status": {
      "clickpost_status_code": 6,
      "location": "VASAI, MUMBAI",
      "status": "O",
      "clickpost_status_description": "OutForDelivery",
      "timestamp": "2017-08-02T13:23:02Z",
      "remark": "Out For Delivery"
    }
  }
}
```

>__NDR(Non delivery report) details in Webhook, send when the status_code = 9 (Failed Delivery)__

```json
{
  "status": "When forward shipment is not accepted by end customer",
  "remark": "Failed Delivery",
  "waybill": "XYZABC",
  "location": "Bengaluru_Koramangala_Dc (Karnataka)",
  "timestamp": "2016-07-12T17:12:36.710",
  "clickpost_status_code": 9,
  "clickpost_status_description": "FailedDelivery",
  "cp_id": 1,

  "additional": {
    "latest_status": {
      "clickpost_status_code": 9,
      "location": "Bengaluru_Koramangala_Dc (Karnataka)",
      "status": "When forward shipment is not accepted by end customer",
      "clickpost_status_description": "FailedDelivery",
      "timestamp": "2016-07-12T17:12:36.710",
      "remark": "Failed Delivery"
    },
    "ndr_status_code": 1,
    "ndr_status_description": "Customer Unavailable"
  }
}
```

###Activating Webhooks:

1. Visit Clickpost dashboard: *Settings* Tab on the left and Click notification section
2. Select webhooks and activate Selected webhooks configuration or All Webhooks configuration as per your need: 
3. Selected webhooks configuration: trigger webhooks only when shipment reaches certain checkpoints in its journey.
4. All webhooks configuration: trigger webhooks for all shipment statuses as they come.

We generally recommend customers to use selected webhooks configuration as all webhooks will trigger too many status messages on your system.

###Webhook data POST on Client Server for all events:

Every time courier partner updates tracking of the shipment, We will post data to your server using the url you registered while registering for webhooks.

###Payload Explanation:

1. waybill: AWB number for which data is posted.
2. status: status of the shipment at that time
3. remarks: remark given by courier partner
4. location: location of shipment at the time of the scan
5. timestamp: date/time in IST format when the scan was done
6. clickpost_status_code: clickpost generated status code for particular status. Clickpost has mapped various statuses of different courier companies into few status codes, which helps customers understand and take action on statuses in preemptive manner. (Explained in next section)
7. clickpost_status_description: description of clickpost_status_code (Specified on next page)


---

###Webhook data POST on Client Server for selected events:

In case customer wants to recieve notifications only for certain events, Clickpost provides funtionality for the same.

If customer opts for this service, we add: "notification_event_id" key in additional object of the payload. This will inform you the current status of shipment.

####Possible values:
1. Out For Pickup
2. Shipped
3. Out For Delivery
4. Failed Delivery
5. Delivered
6. RTO
10. Order Cancelled
12. RTO-Delivered

Following notification_event_id are useful for customers using Clickpost's managed returns service which accepts return requests from end user:

11. Return Request placed: As soon as a return request is placed by the end user using Clickpost's return UI
9. AWB Generated: As soon as an AWB is generated in Clickpost for a return request

Please see the sample payload on the right:

>__Selected event subscribed webhook: Failed delivery Payload__

```json

{
  "waybill": "2614010163240",
  "remark": "Customer escalation received",
  "clickpost_status_code": 9,
  "status": "Pending",
  "clickpost_status_description": "FailedDelivery",
  "location": "Lucknow_Aliganj (Uttar Pradesh)",
  "timestamp": "2019-05-01T00:55:06.367000Z",
  "cp_id": 4,
  "additional": {
    
    "ndr_status_code": 1,
    "ndr_status_description": "Customer unavailable",

    "notification_event_id": 4,

    "latest_status": {
      "remark": "Customer escalation received",
      "clickpost_status_code": 9,
      "status": "Pending",
      "location": "Lucknow_Aliganj (Uttar Pradesh)",
      "clickpost_status_bucket_description": "Failed delivery",
      "clickpost_status_description": "FailedDelivery",
      "timestamp": "2019-05-01T00:55:06.367000Z",
      "clickpost_status_bucket": 5
    },
    "is_rvp": false
  }
}

```
>__Selected event subscribed webhook: Delivered Payload__

```json
{
  "remark": "Delivered to consignee",
  "waybill": "420714276075",
  "clickpost_status_description": "Delivered",
  "timestamp": "2018-08-06T15:00:32.002000Z",
  "cp_id": 4,
  "status": "Delivered",
  "clickpost_status_code": 8,
  "location": "Udaipur_DC (Rajasthan)",

  "additional": {

    "notification_event_id": 5,

    "latest_status": {
      "remark": "Delivered to consignee",
      "timestamp": "2018-08-06T15:00:32.002000Z",
      "clickpost_status_description": "Delivered",
      "status": "Delivered",
      "clickpost_status_code": 8,
      "location": "Udaipur_DC (Rajasthan)"
    }
  }
}

```

###Important Notes and special data in Webhooks (Examples are present on the right):

1. Webhooks do not guarantee the order of data send to Client servers. 
latest_status indicates the latest status for the shipment at the time when the webhook is sent. This is sent with all webhooks
2. In case of NuvoEx Reverse Pickup: doorstep Quality Check order, additional has dsqc object at the time of pickup cancelled (clickpost_status_code = 10) and pickedup (clickpost_status_code = 4)
3. In case of Failed Delivery, Clickpost unified NDR status code and NDR status description is sent in additional
4. Please make your API end point idempotent
5. Since webhooks are transactional in nature, To insure minimal API data loss, we have retries in place if we do not get http 200 response from your server
6. If you opt for selected events webhook notification, in case clickpost receives multiple notification from courier partner at the same time, only the latest notification will be sent to you

###NDR Status Codes

ndr_status_code | ndr_status_description
--------------|------------------------
0 | "Unknown Exception"
1 | "Customer Unavailable"
2 | "Rejected by Customer"
3 | "Delivery Rescheduled"
4 | "No Attempt"
5 | "Customer Unreachable"
6 | "Address Issue"
7 | "Payment Issue"
8 | "Out Of Delivery Area"
9 | "Order Already Cancelled"
10| "Self Collect"
11| "Shipment Seized By Customer"

*Clickpost recommends that the mapping of NDR be done strictly on ndr_status_code and not on ndr_status_description*


---

##Testing Webhook

>__Test Webhook URL__

```
https://www.clickpost.in/api/v1/test_webhook?key=<YOUR_API_KEY>
```

>__Test Webhook Payload__

```json
{
  "test_url": "http://www.clickpost.in/",
  "test_data": {
    "status": "When forward shipment is not accepted by end customer",
    "remark": "Failed Delivery",
    "waybill": "XYZABC",
    "location": "Bengaluru_Koramangala_Dc (Karnataka)",
    "timestamp": "2016-07-12T17:12:36.710",
    "clickpost_status_code": 9,
    "clickpost_status_description": "FailedDelivery",
    "cp_id": 1,

    "additional": {
      "latest_status": {
        "clickpost_status_code": 9,
        "location": "Bengaluru_Koramangala_Dc (Karnataka)",
        "status": "When forward shipment is not accepted by end customer",
        "clickpost_status_description": "FailedDelivery",
        "timestamp": "2016-07-12T17:12:36.710",
        "remark": "Failed Delivery"
      },
      "ndr_status_code": 1,
      "ndr_status_description": "Customer Unavailable"
    }
  }
}

```
You can test the webhooks by making a POST request on the following URL:

`https://www.clickpost.in/api/v1/test_webhook?key=<YOUR_API_KEY>`

Where test_url is your server URL where you want to test the webhook data. This will send sample payload as specified in test_data with Headers on the server mentioned in test_url.

------
