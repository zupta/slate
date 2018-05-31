# Un-Track an Order or Mark a shipment expired

# You have to be registered for tracking service to use this api, if you have not please check Track Order Section.

##Register an AWB for tracking

>POST request. URL:

```
https://www.clickpost.in/api/v2/tracking/awb-unregister/
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
cp_id (required) | integer | courier_partner_id as specified on page 1 of this documentation

####Optional:
There are no optional params passed in the api.

###Response Explanation:

1. "meta" stores information about the API, success or failure
  - success: true/false, true if the API worked fine, else false
  - message: SUCCESS if everything is fine, else the error message c. status: 200, if the API data was fine, 400 in case of a bad request
2. "result" is an array of records. Each record holds information of comma-separated waybill entered in the request parameter.        
------
