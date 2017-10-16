# Shipment Manifestation / AWB Generation API

##Order Creation V1 API
> URL to hit:

```
https://www.clickpost.in/api/v1/create-order/?username=<user-name>&key=<api-key>
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```
> __Example:__ POST Body (COD Shipment)

```json
{
  "pickup_name": "Heronakamura",
  "pickup_phone": "9999999999",
  "pickup_address": "1, Top Floor, Canaught Place, New Delhi",
  "pickup_city": "Delhi",
  "pickup_state": "DL",
  "pickup_country": "IN",
  "pickup_pincode": "110001",
  "pickup_time": "2017-02-14T18:00:00+05:30",
  "drop_name": "Rahul Jagat",
  "drop_phone": "8080808080",
  "drop_address": "KFC, Kalkaji Main Road, New Delhi",
  "drop_city": "DELHI",
  "drop_state": "DELHI",
  "drop_country": "IN",
  "drop_pincode": "110020",
  "return_info": {
        "pincode": "110019",
        "city": "DELHI",
        "name": "Deepanshu",
        "state": "DELHI",
        "country": "IN",
        "phone": 8080808080,
        "address": "Test Address top floor kalkaji NewDelhi "
    },
  "tin": "00000000000",
  "invoice_date": "2016-12-16",
  "order_type": "PREPAID",
  "cod_value": 0,
  "items": [{"price":"370.00","description":"IN1543MTOSKTBLA-146-10","sku":"IN1543MTOSKTBLA-146-10","quantity":"1"},{"price":"694.00","description":"IN1516MTODREMLT-147-10","sku":"IN1516MTODREMLT-147-10","quantity":"1"}],
  "invoice_number": "123465",
  "invoice_value": 1006.00,
  "reference_number": "ASDF1234",
  "email": "founders@clickpost.in",
  "weight": 500,
  "length": 5,
  "height": 10,
  "breadth": 15,
  "courier_partner": 2
}
```

> __Response__

```
{
  "meta": {
    "message": "Order Placed Successfully",
    "status": 200,
    "success": true
  },
  "result": {
    "reference_number": "ASDF1234",
    "waybill": "785578015860",
    "label": "https://pyck-res-bucket.s3.amazonaws.com:443/fedex/2017-02-11/785578015860.pdf"
  }
}
```

> __Example:__ POST Body (PREPAID Shipment)

```
{
    "pickup_address": "B-220/2, 1st Floor, Right Door, Savitri
Nagar, New Delhi",
    "pickup_city": "DELHI",
    "pickup_state": "DELHI",
    "pickup_country": "IN",
    "pickup_pincode": "110017",
    "pickup_time": "2015-12-10T12:00:00Z",
    "drop_name": "Rahul",
    "drop_phone": "8376035546",
    "drop_address": "L-19B, Third Floor, Malviya Nagar, New
    Delhi",
    "drop_city": "delhi",
    "pickup_name": "Deepanshu",
    "pickup_phone": "8376035546",
    "drop_state": "DL",
    "drop_country": "IN",
    "drop_pincode": "110092",
    "return_info": {
        "pincode": "110019",
        "city": "DELHI",
        "name": "Clickpost",
        "state": "DELHI",
        "country": "IN",
        "phone": 8080808080,
        "address": "Test Address, Test Location, Test Landmark New Delhi"
    },
    "tin": "120349483",
    "invoice_date": "2015-12-27",
    "order_type": "PREPAID",
    "cod_value": "0",
    "items": [{"price":"370.00","description":"IN1543MTOSKTBLA-146-10","sku":"IN1543MTOSKTBLA-146-10","quantity":"1"},{"price":"694.00","description":"IN1516MTODREMLT-147-10","sku":"IN1516MTODREMLT-147-10","quantity":"1"}],
    "invoice_number": "INV-234/3",
    "invoice_value": "100",
    "reference_number": "SAMPLE-REF-No",
    "email": "founders@clickpost.in",
    "weight": "10",
    "length": "10",
    "height": "10",
    "breadth": "10",
    "courier_partner": 5
}
```

> __Example:__ POST Body: (Reverse Pickup: RVP Shipment):

```
{
    "courier_partner": 7,
    "email": "founders@clickpost.in",
    "pickup_name": "Deepanshu",
    "pickup_phone": "8080808080",
    "pickup_address": "B-220/2, 1st Floor, Right Door, Savitri Nagar,
    New Delhi",
    "pickup_pincode": "110017",
    "pickup_city": "DELHI",
    "pickup_state": "DELHI",
    "pickup_country": "IN",
    "drop_name": "Rahul",
    "drop_phone": "8080808080",
    "drop_address": "L-19B, third Floor Malviya Nagar, New Delhi",
    "drop_pincode": "110017",
    "drop_city": "DELHI",
    "drop_state": "DELHI",
    "drop_country": "IN",
    "order_type": "PREPAID",
    "cod_value": 0,
    "tin": "120349483",
    "invoice_number": "INV-4/3",
    "invoice_value": 100,
    "invoice_date": "2015-12-27",
    "items": [{"price": 200, "description": "item1", "sku":
    "XYZ1", "quantity": 1}],
    "height": 10,
    "length": 10,
    "breadth": 10,
    "weight": 100,
    "reference_number": "sok56sjkaphf",
    "pickup_time": "2016-10-01T12:00:00Z",
    "rvp_reason": "Not Interested",
    "delivery_type": "RVP"
}
```

> __Example:__ POST Body: (Reverse Pickup with QC detail RVP Shipment[Only for NuvoEx]):

```
{
    "courier_partner": 7,
    "email": "founders@clickpost.in",
    "pickup_name": "Deepanshu",
    "pickup_phone": "8080808080",
    "pickup_address": "B-220/2, 1st Floor, Right Door, Savitri Nagar,
    New Delhi",
    "pickup_pincode": "110017",
    "pickup_city": "DELHI",
    "pickup_state": "DELHI",
    "pickup_country": "IN",
    "drop_name": "Rahul",
    "drop_phone": "8080808080",
    "drop_address": "L-19B, third Floor Malviya Nagar, New Delhi",
    "drop_pincode": "110017",
    "drop_city": "DELHI",
    "drop_state": "DELHI",
    "drop_country": "IN",
    "order_type": "PREPAID",
    "cod_value": 0,
    "tin": "120349483",
    "invoice_number": "INV-4/3",
    "invoice_value": 100,
    "invoice_date": "2015-12-27",
    "items": [
    {"price": 200, 
    "description": "item1",
    "sku": "XYZ1",
    "quantity": 1,
    "qc_type": "doorstep",
    "cat": "electronics",
    "sub_cat": "tv",    
    "image_urls":[
        "https://assetscdn.paytm.com/images/catalog/view_item/114560/1494268990652.jpg",
        "https://assetscdn.paytm.com/images/catalog/view_item/116303/1493891914950.jpg"
      ]
    }
    ],    
    "height": 10,
    "length": 10,
    "breadth": 10,
    "weight": 100,
    "reference_number": "sok56sjkaphf",
    "pickup_time": "2016-10-01T12:00:00Z",
    "rvp_reason": "Not Interested",
    "delivery_type": "RVP"
}
```

The create order API allows uploading the package details (manifest information) into the courier partner’s system and returns a label generated by them. You can create single order; errors/warnings will be highlighted in the response.

Please note, in case of any validation failure - order will not get created. Please wait for 8 seconds before you reject a rest-request for latency.


The API is a HTTP POST request to: `https://www.clickpost.in/api/v1/create-order/` where output format is json.

Listed below are the parameters:
####URL parameters:
Parameter | Type | Description
--------- | ---- | -----------
Username | character | User name provided to you
key | character | API key provided to you

####POST Parameters:

Format: JSON

####Compulsory Fields:

#####Pickup information
Parameter | Type | Description
--------- | ---- | -----------
pickup_name | character | maximum length of 100 characters
pickup_phone |integer | 10/11 digit phone number
pickup_pincode | integer | 6 digit pincode
pickup_address | character | maximum length of 500 characters
pickup_time | character | (ISO Format: example 2015-12-10T12:00:00Z)
pickup_city | character | pickup city name, maximum length 200 characters
pickup_state | character | pickup state name, maximum length 200 characters
pickup_country | character | pickup country name, maximum length 100 characters i. email: email id to be sent to courier partner for this shipment
vendor_code | character | (optional) vendor code of pickup location. If this field is not provided, Clickpost will generate vendor code for the pickup location
#####Drop Information
Parameter | Type | Description
--------- | ---- | -----------
drop_name | character | maximum length of 100 characters
drop_address | character | maximum length of 500 characters
drop_phone | integer | 10/11 digit phone number
drop_pincode| integer | 6 digit pincode
drop_city | character | drop city name, maximum length 200 characters
drop_state | character | drop state name, maximum length 200 characters
drop_country | character | drop country name, maximum length 200 characters
drop_email | character | (optional) email of the customer
#####Return Information
Parameter | Type | Description
--------- | ---- | -----------
name | character | maximum length of 100 characters
address | character | maximum length of 500 characters
phone | integer | 10/11 digit phone number
pincode| integer | 6 digit pincode
city | character | drop city name, maximum length 200 characters
state | character | drop state name, maximum length 200 characters
country | character | drop country name, maximum length 200 characters
email | character | (optional) email of the customer
#####Shipment details
Parameter | Type | Description
--------- | ---- | -----------
items | List | Json list with multiple item objects in it. Each item object should have
price | double | price of the item
description | character | Item description
sku | character | SKU unit name of item
quantity | Integer | number of item pieces
invoice_value | decimal/float/integer | value
invoice_number | character | string of length 50 characters
invoice_date | character | (Format: YYYY-MM-DD, example: 2015-12-25 for 25th December  2015)
reference_number | character | reference number to tag the order with your order id.
length | integer | in cm
breadth | integer | in cm
height | integer | in cm
weight | integer | grams
tin | character | TIN number of seller
#####Order type:
Parameter | Type | Description
--------- | ---- | -----------
order_type | character | COD/PREPAID
cod_value: if order_type = COD | double | cod_value should be greater than 0
cod_value: if order_type = PREPAID | double | cod_value should be equal to 0
#####Courier Partner:
Parameter | Type | Description
--------- | ---- | -----------
courier_partner | integer | ID of courier partner for which the order is to be placed.

List of courier partners is present at:
<a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>

#####**Compulsory fields for RVP order creation:**
Parameter | Type | Description
--------- | ---- | -----------
rvp_reason | character | stating the reason for Reverse Pickup
delivery_type | character | For Reverse Pickup, the value of this field should  be **"RVP"**

#####Optional field for NuvoEx RVP (Doorstep QC):
Parameter | Type | Description
--------- | ---- | -----------
qc_type | character | pass "doorstep" if you want reverse pickup to be done as doorstep quality check as leave it blank
image_urls | character | add this field in items array for each item. value will be comma seperated url strings without spaces.
cat | character | category of product for qc questions to be asked at doorstep. To be passed in items array for each item object
sub_cat | character | sub category of product for qc questions to be asked at doorstep. To be passed in items array for each item object
#####Optional field for Bluedart (Critical / Time defined delivery service):
Parameter | Type | Description
--------- | ---- | -----------
service_type | character | If you are using Critical shipment service, Time Defined delivery Service (10:30 am or 12 noon next day), Please pass this field with values: 

1. C: Critical Shipment 
2. T: Time defined delivery on or before 10:30 
3. N: Time defined delivery on or before 12

###Response Explanation:

Response Object has two parts:

1. meta: stores information about the API, success or failure
  1. "success": true/false, tells whether the order was created or not
  2. "message": SUCCESS in case order was created successfully, else returns error
  3. "status":
      - 200 if the order is created successfully,
      - 400 if there is a bad request encountered: errors will be present in “message”
2. result:
  1. reference_number: reference number provided in the post data
  2. waybill: waybill generated by courier partner for the shipment
  3. label: AWS link of the label generated for the shipment (Not generated for RVP shipments)
  Additional fields for Bluedart:
  4. DestinationLocation: 3 digit destination location code needed by Bluedart on shipping label
  5. DestinationArea: 3 digit destination area code needed by Bluedart on shipping label


<aside class="warning">
You must replace Username/key with the username/key provided to you.
</aside>

----------
