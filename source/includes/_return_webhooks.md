# Track Return Order

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
  "waybill": "",
  "clickpost_status_code": 101,
  "cp_id": -1,
  "clickpost_status_description": "Return Order Placed",
  "status": "O",
  "location": "VASAI, MUMBAI",
  "timestamp": "2017-08-02T13:23:02Z",
  "remark": "Return Order Placed",
  "additional": {
    "is_rvp":True,
    "forward_awb":"sample_forward_awb",
    "forward_reference_number":"sample_forward_reference",
    "latest_status": {
      "clickpost_status_code": 101,
      "location": "",
      "status": "O",
      "clickpost_status_description": "Return Order Placed",
      "timestamp": "2017-08-02T13:23:02Z",
      "remark": "Return Order Placed"
    }
  }
}
```

###Activating Webhooks:

1. Visit Clickpost dashboard: *Settings* Tab on the left and Click notification section
2. Select webhooks and activate Selected webhooks configuration or All Webhooks configuration as per your need

###Payload Explanation:

1. waybill: AWB number for which data is posted (Will be blank for return order placed).
2. status: status of the shipment at that time
3. remarks: remark given by courier partner
4. location: location of shipment at the time of the scan
5. timestamp: date/time in IST format when the scan was done
6. clickpost_status_code: clickpost generated status code for particular status. Clickpost has mapped various statuses of different courier companies into few status codes, which helps customers understand and take action on statuses in preemptive manner.
7. clickpost_status_description: description of clickpost_status_code
8. is_rvp inside additional object tells the payload is for reverse orders. forward_awb field contain the forward awb number for which return order has been placed and forward_reference_number will have the corresponding reference number.
9. waybill number will be blank as order is not yet created on courier company (not manifested yet) 
10. clickpost_status_code will have 101 value which is Return Order Placed.


---

###Webhook data POST on Client Server for selected events:

In case customer wants to recieve notifications only for certain events, Clickpost provides funtionality for the same.

If customer opts for this service, we add: "notification_event_id" key in additional object of the payload. This will inform you the current status of shipment. For return (Return Request Placed) this field's value will be 11 

###Important Notes and special data in Webhooks (Examples are present on the right):

1. Webhooks do not guarantee the order of data send to Client servers. 
latest_status indicates the latest status for the shipment at the time when the webhook is sent. This is sent with all webhooks
2. Please make your API end point idempotent
3. Since webhooks are transactional in nature, To insure minimal API data loss, we have retries in place if we do not get http 200 response from your server
4. If you opt for selected events webhook notification, in case clickpost receives multiple notification from courier partner at the same time, only the latest notification will be sent to you

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
    "status": "Return Order Placed",
    "remark": "Return Order Placed",
    "waybill": "",
    "location": "",
    "timestamp": "2016-07-12T17:12:36.710",
    "clickpost_status_code": 101,
    "clickpost_status_description": "Return Order Placed",
    "cp_id": 1,
    "additional": {
      "is_rvp":True,
      "forward_awb":"sample_forward_awb",
      "forward_reference_number":"sample_forward_reference",
      "latest_status": {
        "clickpost_status_code": 101,
        "location": "",
        "status": "Return Order Placed",
        "clickpost_status_description": "Return Order Placed",
        "timestamp": "2016-07-12T17:12:36.710",
        "remark": "Return Order Placed"
      }      
    }
  }
}

```
You can test the webhooks by making a POST request on the following URL:

`https://www.clickpost.in/api/v1/test_webhook?key=<YOUR_API_KEY>`

Where test_url is your server URL where you want to test the webhook data.

------