#API of fetching POD

> URL to hit:

```
https://www.clickpost.in/api/v1/pod/pod_from_shipment_details?key=42d42a34-ae09-469312b20c-ae2624&cp_id=8&waybill=<waybill>

Headers: {'Content-type': 'application/json'}

(key needs to be replaced with the key provided to you) Response:
```
> __Example: GET Body__ (POD shipment)

```json
{
     "result": {
                "pod_url": "pod_url"
            },
     "meta": {"status": 200,
              "message": "success",
              "success": true}
 }
```

Shipment POD API allows you to fetch pod a shipment against which the order has been delivered.

The API is a HTTP GET request to: https://www.clickpost.in/api/v1/pod/pod_from_shipment_details/ where output is json

Listed below are the parameters:

####URL parameters:
1. username: User name provided to you.
2. key: API key provided to you.
3. waybill: waybill, for which pod needs to be fetched
4. cp_id: Courier Partner ID of the courier from which shipment was dispatched. List: <a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>


###Response Explanation:

Response will have `meta` tag which explains about the status of the shipment:

1. message: `SUCCESS` in case the Shipment is deleted successfully, else the error message provided by courier partner.
2. success: true if order is deleted successfully, else false
3. status: 200 if API works fine, 400 in case of bad request
4. result: it will have pod s3 url.