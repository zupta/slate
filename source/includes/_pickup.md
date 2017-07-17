#Pickup Request API

> URL to hit:

```
https://www.clickpost.in/api/v1/create-pickup/?username=test&key=42d42a34-ae09-4693- b20c-ae
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you) POST Body:
```

> __Example: POST Body__ (Pickup Request)

```json
{
  "pickup_date": "2016-04-02T12:00:00Z",
  "courier_partner": 1,
  "items": "laptop",
  "pickup_pincode": "110017",
  "pickup_email": "founders@clickpost.in",
  "pickup_phone": "8376035546",
  "pickup_name": "Test-User",
  "pickup_city": "Delhi",
  "pickup_state": "DELHI",
  "pickup_address": "B-222/2 savitri nagar new delhi -10"
}
```

The Pickup Request API allows you to place pickup request for courier partners and obtain confirmation for the same.

Please note, in case of any validation failure - order will not get created.

The API is a HTTP POST request to:
`https://www.clickpost.in/api/v1/create-pickup/ ` where output format is json.

Listed below are the parameters:

####URL parameters:

Parameter | Type | Description
--------- | ---- | -----------
username | character | user name provided to you
key | character | API key provided to you

####POST Parameters:

Format: JSON

###Compulsory Fields:

Parameter | Type | Description
--------- | ---- | -----------
pickup_date | character | ISO datetime field example: 2015-03-31T12:00:00Z
courier_partner | integer |ID of courier partner for which the pickup request needs to be placed. List at : <a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>
items | character | description of item that needs to be placed. Max length: 200 chars
pickup_address | character | Address of pickup location
pickup_name | character | Contact person for the pickup
pickup_email | character | email contact of the pickup location
pickup_pincode | integer | pincode of pickup location
pickup_phone | integer | contact number of pickup location, 10/11 digit number
pickup_city | character | name of pickup city
pickup_state | character | name of pickup state

> __Response__

```json
{
  "meta": {
    "message": "SUCCESS",
    "success": true,
    "status": 200
  },
  "result": {
    "location": "DELKL",
    "confirmation_number": "6" 
  }
}
```

###Response Explanation:

Response will have meta tag which explains about the status of the API and `result` which provides pickup details. In `meta` tag:

1. message: SUCCESS if the pickup request is placed successfully, error message otherwise
2. success: true if pickup request is placed successfully, else false
3. status: 200 if pickup request is placed successfully, 400 in case of bad request

In `result` tag:

1. location: ID of pickup location shared by courier partner
2. confirmation_number: pickup confirmation number

Result tag will be present in request only if the meta tag contains `success` : true.