#Cancel Shipment API

> URL to hit:

```
https://www.clickpost.in/api/v1/cancel-order/?username=test&key=42d42a34-ae09-469312b20c-ae2624&waybill=782715732348&cp_id=8&account_code=cli12

Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you) Response:
```
> __Example: GET Body__ (Cancel Order)

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
4. cp_id: Courier Partner ID of the courier from which shipment was dispatched. List: <a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>
5. account_code (optional): in case you have multiple courier accounts for a courier partner on Clickpost, please pass account_code in the cancellation API so that clickpost uses correct credentials to mark the shipment cancel


###Response Explanation:

Response will have `meta` tag which explains about the status of the shipment:

1. message: `SUCCESS` in case the Shipment is deleted successfully, else the error message provided by courier partner.
2. success: true if order is deleted successfully, else false
3. status: 200 if API works fine, 400 in case of bad request