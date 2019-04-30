# Track Return Order

##Return Order Placed Webhook

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
        "location": "",
        "remark": "Return Order Placed",
        "notification_event": 11,
        "timestamp": "2019-04-29 07:47:07.161221",
        "clickpost_status_code": 101,
        "cp_id": -1,
        "clickpost_status_bucket_description": "Return Order Placed",
        "waybill": "",
        "clickpost_status_bucket": 8,
        "status": "Return Order Placed",
        "clickpost_status_description": "Return Order Placed",
        "additional": {
            "latest_status": {
                "clickpost_status_bucket_description": "Return Order Placed",
                "clickpost_status_description": "Return Order Placed",
                "clickpost_status_bucket": 8,
                "remark": "Return Order Placed",
                "status": "Return Order Placed",
                "location": "",
                "timestamp": "2019-04-29 07:47:07.161252",
                "clickpost_status_code": 101
            },
            "is_rvp": true,
            "notification_event_id": 11,
            "forward_awb": "5522110373319",
            "self_shipped": false,
            "forward_reference_number": "1405277",
            "item_info": [{
              "sku": "120667",
              "quantity": 1
          }, {
              "sku": "9649",
              "quantity": 1
          }, {
              "sku": "46457",
              "quantity": 1
          }, {
              "sku": "10924",
              "quantity": 1
          }],
        }
    }
```

This webhook is only useful for customers using Clickpost managed returns platform to accept customer returns on their website.

###Activating Return order placed webhook:

1. Visit Clickpost dashboard: *Settings* Tab on the right and Click notification section
2. Select webhooks and activate Selected webhooks configuration --> "Return Order Placed". 

###Payload Explanation:

1. waybill: AWB number for which data is posted (Will be blank for return order placed).
2. status: status of the shipment at that time
3. remarks: remark given by courier partner
4. location: location of shipment at the time of the scan
5. timestamp: date/time in IST format when the scan was done
6. clickpost_status_code: clickpost generated status code for particular status. Clickpost has mapped various statuses of different courier companies into few status codes, which helps customers understand and take action on statuses in preemptive manner.
7. clickpost_status_description: description of clickpost_status_code
8. is_rvp inside additional object tells the payload is for reverse orders. 
9. forward_awb field contain the forward awb number for which return order has been placed 
10. forward_reference_number will have the corresponding reference number.
12. waybill number will be blank as order is not yet created on courier partner (not manifested yet) 
13. clickpost_status_code will have 101 value which is Return Order Placed.
14. self_shipped: Either True or False depending upon how the return shipment is shipped, if shipped by customer, then self_shipped is True else False.
15. item_info: represents the item details for which return request is raised by the customer

---

Logic to be applied on webhook endpoint to detect returns webhook: In all reverse pickup order webhooks, is_rvp will be true. If its true, check the forward_awb or forward_reference_number in the payload, verify it with the same in your system and update the sku(s) present in item_info.

------