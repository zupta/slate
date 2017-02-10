# Track Order

To track any shipment, client needs to register for tracking service on Clickpost server 1st.



Courier Partner | courier_partner_id
----- | :------:
Fedex | 1
Aramex | 2
EcomExpress | 3
Delhivery | 4
Bluedart | 5
XpressBees | 6
NuvoEx | 7
InnovEx | 10
ShadowFax | 11
OnlineExpress | 12

##Register for Tracking Service

> It’s a POST request. The URL:

```
https://www.clickpost.in/api/v1/register-service/
Headers: {'Content-type': 'application/json'}
```
>__Example__

```
{
  "key":"---Your Clickpost API KEY--",
  "service_id":2
}
```
>__Response__

```json
{
  "message": "SUCCESS",
  "status_code": 200,
  "success": true
}
```

###Fields Explanation:

Parameter | Type | Description
--------- | ---- | -----------
key (required) | character | this is the API Key provided to you
service_id (required) | Integer | this is the Integer id of service for which you want to register

####Service ID

ID | Use
------ | -------
1 | For placing orders on courier partner
2 | For Tracking Shipments on Clickpost
3 | For using Clickpost Recommendation Engine

##Register an AWB for tracking

>It’s a POST request. The URL:

```
https://www.clickpost.in/api/v1/tracking/awb-register/
Headers: {'Content-type': 'application/json'}
```

>__Example__

```json
{
     "waybill": "P76933624",
     "key": "2e9b19ac-8e1f-41ac-a35b-4cd23f41",
     "cp_id": 11
}
```
>__Response__

```json
{
     "tracking_id": 20370,
     "status_code": 200,
     "success": true,
     "message": "SUCCESS"
}
```

###Fields Explanation

Parameter | Type | Description
--------- | ---- | -----------
key (required) | character | this is the API Key
waybill (required) | character | this is/are comma separated waybill numbers for which the status is required
cp_id (required) | integer | courier_partner_id as specified on page 1 of this documentation


##Tracking AWB Using Polling

>__Example__

```
https://www.clickpost.in/api/v2/track-order/?username=testuser&key=2e9b19ac-8e1f- 41ac-a35b-4cd23f41ae17&waybill=3515341&cp_id=10

Headers: {'Content-type': 'application/json'}
```

>__Response__

```json
{
	"meta": {
		"status": 200,
		"messsage": "SUCCESS",
		"success": true
	},
	"result": {
		"506610002236": {
			"scans": [{
				"status": "OrderPlaced",
				"remark": "OrderPlaced",
				"location": "None",
				"timestamp": "2016-04-12T07:37:22.113Z",
				"clickpost_status_description": "OrderPlaced",
				"clickpost_status_code": 1
			}, {
				"status": "Picked up and Booking processed",
				"remark": "Picked up and Booking processed",
				"location": "SOUTH DELHI, DELHI",
				"timestamp": "2016-10-27 22:15:13+00:00",
				"clickpost_status_description": "PickedUp",
				"clickpost_status_code": 4
			}, {
				"status": "In Transit to",
				"remark": "In Transit to",
				"location": "DELHI, DELHI",
				"timestamp": "2016-10-27 22:18:57+00:00",
				"clickpost_status_description": "InTransit",
				"clickpost_status_code": 5
			}, {
				"status": "Out For Delivery",
				"remark": "Out For Delivery",
				"location": "MUMBAI, MUMBAI",
				"timestamp": "2016-10-31 13:29:24+00:00",
				"clickpost_status_description": "OutForDelivery",
				"clickpost_status_code": 6
			}, {
				"status": "Delivered",
				"remark": "Delivered on 03 Nov 16 - Signed by sign",
				"location": "MUMBAI, MUMBAI",
				"timestamp": "2016-11-03 08:10:56+00:00",
				"clickpost_status_description": "Delivered",
				"clickpost_status_code": 8
			}],
			"latest_status": {
				"status": "Delivered",
				"remark": "Delivered on 03 Nov 16 - Signed by sign",
				"location": "MUMBAI, MUMBAI",
				"timestamp": "2016-11-03T08:10:56Z",
				"clickpost_status_description": "Delivered",
				"clickpost_status_code": 8
			}
		}
	}
}
```

Package tracker API retrieves the historic statuses and the current status of the package.

The API is a HTTP GET request to:
https://www.clickpost.in/api/v2/track-order/ where output is json

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


##Tracking Waybills Using Webhooks
###Register for Webhooks:

>It's a POST request. The URL

```
URL: https://www.clickpost.in/api/v1/tracking/register-webhook/
Headers: {'Content-type': 'application/json'}
```

>__Example__

```json
{
     "service_id": 2,
     "key": "xxxxxxxxxxxx---Your API KEY---xxxxxxxxxxxxxxxxxxx",
     "webhook_url": "xxxxxxx---- Your Webhook URL---xxxxxxxx"
}
```

####Fields Explanation:

1. “service_id” is the service identifier for which you want to register the webhook. Right  now, Clickpost provides webhook only for tracking service, which has service_id = 2
2. “key”: API key provided to you
3. “webhook_url” is the url on which data will be posted on your server

>__Response__

```json
{
     "message": "SUCCESS",
     "webhook_key": "7e7cc4c4-273d-49ce-90f1-ecc2b69b4e6c",
     "success": true,
     "status_code": 200
}
```
###Response Explanation:

1. “message”: SUCCESS implies the request has been placed successfully. Else message will hold error message
2. “webhook_key”: security key that Clickpost will send with every request it will post on  your server. This key will be sent in headers as: `webhook_key: webhook_key_as_in_registration_response`
3. “success” : true if the request has been placed successfully false other wise
4. "status_codes" :

Status Code | Description
------ | -------
200 | Everything is fine
301 | Invalid API key
302 | AWB already exists
305 | Already registered Webhook for this AWB
306 | Not authorized to use this service


###Webhook data POST on Client Server:

Every time courier partner updates tracking of the shipment, We will post data to your server using the url you registered while registering for webhooks.

>__Header__

```json
{
     "Content-Type": "application/json",
     "webhook_key": "webhook_key_given_during_webhooks_register"
}
```

>__Payload__

```json
{
"status": "When forward shipment is accepted by end customer and POD is received",
  "remark": "Delivered",
  "waybill": "XYZABC",
  "location": "Bengaluru_Koramangala_Dc (Karnataka)",
  "timestamp": "2016-07-12T17:12:36.710Z",
  "clickpost_status_code": 8,
  "clickpost_status_description": "Delivered"
}
```

###Payload Explanation:

1. waybill: AWB number for which data is posted.
2. status: status of the shipment at that time
3. remarks: remark given by courier partner
4. location: location of shipment at the time of the scan
5. timestamp: date/time in ISO format when the scan was done
6. clickpost_status_code: clickpost generated status code for particular status. Clickpost has mapped various statuses of different courier companies into few status codes, which helps customers understand and take action on statuses in preemptive manner. (Explained on next page)
7. clickpost_status_description: description of clickpost_status_code (Specified on next page)


####Uber Status Mapping

clickpost_status_id | clickpost_status_description | Meaning
----- | ------ |  -------
1 | ORDER_PLACED | 'Order Has Been Placed'
2 | PICKUP_PENDING | 'Pickup Pending'
3 | PICKUP_CANCELLED | 'Pickup Cancelled'
4 | PICKED_UP | 'Pickup Has Been Done'
5 | INTRANSIT | 'In Transit'
6 | OUT_FOR_DELIVERY | 'Shipment Out For Delivery'
7 | NOT_SERVICEABLE | 'Area For Delivery Is Not Servicable'
8 | DELIVERED | 'Shipment Delivered'
9 | FAILED_DELIVERY | 'Delivery Failed'
10 | CANCELLED_ORDER | 'Order Has Been Cancelled'
11 | RTO_REQUESTED | 'Rto For Shipment has been Requested'
12 | RTO | 'Marked As Return'
13 | RTO_OUT_FOR_DELIVERY | 'Shipment Is Out For Delivery For RTO'
14 | RTO_DELIVERED | 'Rto Delivered'
15 | RTO_FAILED | 'Rto Failed'
16 | LOST | 'Shipment is Lost'
17 | DAMAGED | 'Shipment is damaged'
18 | SHIPMENT_DELAYED |'Shipment Is Delayed Or Misroute'
19 | CONTACT_CUSTOMER_CARE | 'Contact To The Customer Care'
20 | SHIPMENT_HELD | 'Shipment Is being held'
21 | RTO_INTRANSIT | 'Shipment Return On The Way'

------
