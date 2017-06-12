#Cancel Shipment API

> URL to hit:

```
https://www.clickpost.in/api/v1/cancel-order/?username=test&key=42d42a34-ae09-4693- b20c-ae2624&awb=782715732348

Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you) Response:
```
> __Example: POST Body__ (Cancel Order)

```json
{
"meta": {
    "message": "8159:Shipment Delete was requested for a tracking
number already in a deleted state.",
    "success": false,
    "status": 400
  }
}
```

Cancel API allows you to cancel a shipment for which the order has been created.

The API is a HTTP GET request to: https://www.clickpost.in/api/v1/cancel-order/ where output is json

Listed below are the parameters:

####URL parameters:
1. username: User name provided to you.
2. key: API key provided to you.
3. waybill: waybill, which needs to be cancelled


###Response Explanation:

Response will have `meta` tag which explains about the status of the shipment:

1. message: `SUCCESS` in case the Shipment is deleted successfully, else the error message provided by courier partner.
2. success: true if order is deleted successfully, else false
3. status: 200 if API works fine, 400 in case of bad request