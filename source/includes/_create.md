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
        "address": "Test Address top floor kalkaji New Delhi "
    },
  "tin": "00000000",
  "invoice_date": "2016-12-16",
  "order_type": "PREPAID",
  "cod_value": 0,
  "items": [{"price":"370.00","description":"IN1543MTOSKTBLA-146-10","sku":"IN1543MTOSKTBLA-146-10","quantity":"1","images": "http://sample-file1.jpg,http://sample-file2.jpg"},{"price":"694.00","description":"IN1516MTODREMLT-147-10","sku":"IN1516MTODREMLT-147-10","quantity":"1","images": "http://sample-file1.jpg,http://sample-file2.jpg"}],
  "invoice_number": "123465",
  "invoice_value": 1006.00,
  "reference_number": "SAMPLE-REF-No",
  "email": "founders@clickpost.in",
  "weight": 500,
  "length": 5,
  "height": 10,
  "breadth": 15,
  "courier_partner": 2,
  "gst_info": {
        "seller_gstin": "1234",
        "taxable_value": 100,
        "ewaybill_serial_number": "2345677",
        "is_seller_registered_under_gst": false,
        "sgst_tax_rate": 100,
        "place_of_supply": "DELHI",
        "gst_discount": 0,
        "hsn_code": "1234",
        "sgst_amount": 100,
        "enterprise_gstin": "13",
        "gst_total_tax": 100,
        "igst_amount": 100,
        "cgst_amount": 200,
        "gst_tax_base": 200,
        "consignee_gstin": "1233",
        "igst_tax_rate": 100,
        "invoice_reference": "1234",
        "cgst_tax_rate": 100
    }
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
    "reference_number": "SAMPLE-REF-No",
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
    "items": [{"price":"370.00","description":"IN1543MTOSKTBLA-146-10","sku":"IN1543MTOSKTBLA-146-10","quantity":"1","images": "http://sample-file1.jpg,http://sample-file2.jpg"},{"price":"694.00","description":"IN1516MTODREMLT-147-10","sku":"IN1516MTODREMLT-147-10","quantity":"1","images":"http://sample-file1.jpg,http://sample-file2.jpg"}],
    "invoice_number": "INV-234/3",
    "invoice_value": "100",
    "reference_number": "SAMPLE-REF-No",
    "email": "founders@clickpost.in",
    "weight": "10",
    "length": "10",
    "height": "10",
    "breadth": "10",
    "courier_partner": 5,
    "gst_info": {
        "seller_gstin": "1234",
        "taxable_value": 100,
        "ewaybill_serial_number": "2345677",
        "is_seller_registered_under_gst": false,
        "sgst_tax_rate": 100,
        "place_of_supply": "DELHI",
        "gst_discount": 0,
        "hsn_code": "1234",
        "sgst_amount": 100,
        "enterprise_gstin": "13",
        "gst_total_tax": 100,
        "igst_amount": 100,
        "cgst_amount": 200,
        "gst_tax_base": 200,
        "consignee_gstin": "1233",
        "igst_tax_rate": 100,
        "invoice_reference": "1234",
        "cgst_tax_rate": 100
    }
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
    "XYZ1", "quantity": 1, "images": "http://sample-file1.jpg,http://sample-file2.jpg"}],
    "height": 10,
    "length": 10,
    "breadth": 10,
    "weight": 100,
    "reference_number": "sok56sjkaphf",
    "pickup_time": "2016-10-01T12:00:00Z",
    "gst_info": {
        "seller_gstin": "1234",
        "taxable_value": 100,
        "ewaybill_serial_number": "2345677",
        "is_seller_registered_under_gst": false,
        "sgst_tax_rate": 100,
        "place_of_supply": "DELHI",
        "gst_discount": 0,
        "hsn_code": "1234",
        "sgst_amount": 100,
        "enterprise_gstin": "13",
        "gst_total_tax": 100,
        "igst_amount": 100,
        "cgst_amount": 200,
        "gst_tax_base": 200,
        "consignee_gstin": "1233",
        "igst_tax_rate": 100,
        "invoice_reference": "1234",
        "cgst_tax_rate": 100
    },

    "rvp_reason": "Not Interested",
    "delivery_type": "RVP"
}
```

> __Example:__ POST Body: (Reverse Pickup with QC detail RVP Shipment[Only for Shadowfax Reverse]):

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
    "delivery_type": "RVP",
    "gst_info": {
        "seller_gstin": "1234",
        "taxable_value": 100,
        "ewaybill_serial_number": "2345677",
        "is_seller_registered_under_gst": false,
        "sgst_tax_rate": 100,
        "place_of_supply": "DELHI",
        "gst_discount": 0,
        "hsn_code": "1234",
        "sgst_amount": 100,
        "enterprise_gstin": "13",
        "gst_total_tax": 100,
        "igst_amount": 100,
        "cgst_amount": 200,
        "consignee_gstin": "1233",
        "igst_tax_rate": 100,
        "invoice_reference": "1234",
        "cgst_tax_rate": 100
    }
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
reference_number | character | reference number to tag the order with your order id. Reference number has to follow Code 39 standards (https://en.wikipedia.org/wiki/Code_39)
length | integer | in cm
breadth | integer | in cm
height | integer | in cm
weight | integer | grams
tin | character | TIN number of seller (Now GST No)
images | character | comma separated images of the item
#####GST Information
Parameter | Type | Description
--------- | ---- | -----------
enterprise_gstin | string | GST No of enterprise shipping the shipment
seller_gstin | string | GST No of seller sending the shipment (will be different from above for marketplaces)
taxable_value | double | taxable amount for GST (generally invoice_value of shipment)
ewaybill_serial_number | string | ewaybill for the shipment (optional)
is_seller_registered_under_gst | boolean | True / False, depending on whether you are registered for GST
place_of_supply | string | place of supply of service/product (https://cleartax.in/s/gst-state-code-jurisdiction)
gst_discount | double | discount given under gst, if any (optional)
hsn_code | string | HSN code for the product shipped (You may search for HSN https://cleartax.in/s/gst-hsn-lookup)
gst_total_tax | double | total GST applicable for the shipment
sgst_tax_rate | integer | tax percent applicable for sgst for the shipment (optional)
sgst_amount | double | amount applicable for sgst for the shipment (optional)
igst_tax_rate | integer | tax percent applicable for igst for the shipment (optional)
igst_amount | double | amount applicable for igst for the shipment (optional)
cgst_tax_rate | integer | tax percent applicable for cgst for the shipment (optional)
cgst_amount | double | amount applicable for cgst for the shipment (optional)
consignee_gstin | string | GST No of consignee (compulsory for B2B shipments) 
invoice_reference | string | invoice number for the shipment
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

##Order Creation V3 API
> URL to hit:

```
https://www.clickpost.in/api/v3/create-order/?username=<user-name>&key=<api-key>
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```
> __Example:__ POST Body (COD Shipment)

```json
{
    "pickup_info": {
        "pickup_state": "DELHI",
        "pickup_address": "A-228 top floor kalkaji New Delhi ",
        "email": "deepanshu.kartikey@pyck.in",
        "pickup_time": "2017-05-20T12:00:00Z",
        "pickup_pincode": "110019",
        "pickup_city": "DELHI",
        "tin": "120349483",
        "pickup_name": "Deepanshu",
        "pickup_country": "IN",
        "pickup_phone": "9816691388"
    },
    "drop_info": {
        "drop_address": "F-68 third floor kalkaji New Delhi ",
        "drop_phone": "9717732407",
        "drop_country": "IN",
        "drop_state": "DELHI",
        "drop_pincode": "110019",
        "drop_city": "Delhi",
        "drop_name": "Prashant"
    },
    "shipment_details": {
        "height": 12,
        "order_type": "COD",
        "invoice_value": 200,
        "invoice_number": "INV123",
        "invoice_date": "2015-12-27",
        "reference_number": "Order-1232",
        "length": 10,
        "breadth": 10,
        "weight": 100,
        "items": [
            {
                "price": 200,
                "description": "item1",
                "additional": {
                    "length": 10,
                    "height": 10,
                    "breadth": 10,
                    "weight": 100,
                    "images": "http://sample-file1.jpg,http://sample-file2.jpg"
                },
                "quantity": 1,
                "sku": "XYZ1"
            }
        ],
        "cod_value": 200,
        "courier_partner": 3
    },
    "gst_info": {
        "seller_gstin": "1234",
        "taxable_value": 100,
        "ewaybill_serial_number": "2345677",
        "is_seller_registered_under_gst": false,
        "sgst_tax_rate": 100,
        "place_of_supply": "DELHI",
        "gst_discount": 0,
        "hsn_code": "1234",
        "sgst_amount": 100,
        "enterprise_gstin": "13",
        "gst_total_tax": 100,
        "igst_amount": 100,
        "cgst_amount": 200,
        "gst_tax_base": 200,
        "consignee_gstin": "1233",
        "igst_tax_rate": 100,
        "invoice_reference": "1234",
        "cgst_tax_rate": 100
    },
    "additional": {
        "label": true,
        "return_info": {
            "pincode": "110019",
            "address": "Test Address top floor kalkaji NewDelhi ",
            "state": "DELHI",
            "phone": "8080808080",
            "name": "Deepanshu",
            "city": "DELHI",
            "country": "IN"
        },
        "awb_number ": "43062728295",
        "delivery_type": "FORWARD",
        "async": true,
        "gst_number" : "21313",
        "account_code": "ecom surface"
    }
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
    "drop_info": {
        "drop_address": "F-68 third floor kalkaji New Delhi ",
        "drop_phone": "9717732407",
        "drop_country": "IN",
        "drop_state": "DELHI",
        "drop_pincode": "110019",
        "drop_city": "Delhi",
        "drop_name": "Prashant"
    },
    "additional": {
        "label ": true,
        "return_info": {
            "pincode": "110019",
            "address": "Test Address top floor kalkaji NewDelhi ",
            "state": "DELHI",
            "phone": "8080808080",
            "name": "Deepanshu",
            "city": "DELHI",
            "country": "IN"
        },
        "awb_number ": "43062728295",
        "delivery_type": "FORWARD",
        "async": true,
        "gst_number" : "21313",
        "account_code": "ecom surface"
    },
    "pickup_info": {
        "pickup_state": "DELHI",
        "pickup_address": "A-228 top floor kalkaji New Delhi ",
        "email": "deepanshu.kartikey@pyck.in",
        "pickup_time": "2017-05-20T12:00:00Z",
        "pickup_pincode": "110019",
        "pickup_city": "DELHI",
        "tin": "120349483",
        "pickup_name": "Deepanshu",
        "pickup_country": "IN",
        "pickup_phone": "9816691388"
    },
    "gst_info": {
        "seller_gstin": "1234",
        "taxable_value": 100,
        "ewaybill_serial_number": "2345677",
        "is_seller_registered_under_gst": false,
        "sgst_tax_rate": 100,
        "place_of_supply": "DELHI",
        "gst_discount": 0,
        "hsn_code": "1234",
        "sgst_amount": 100,
        "enterprise_gstin": "13",
        "gst_total_tax": 100,
        "igst_amount": 100,
        "cgst_amount": 200,
        "gst_tax_base": 200,
        "consignee_gstin": "1233",
        "igst_tax_rate": 100,
        "invoice_reference": "1234",
        "cgst_tax_rate": 100
    },
    "shipment_details": {
        "height": 12,
        "order_type": "PREPAID",
        "invoice_value": 200,
        "invoice_number": "INV123",
        "invoice_date": "2015-12-27",
        "reference_number": "Order-1232",
        "length": 10,
        "breadth": 10,
        "weight": 100,
        "items": [
            {
                "price": 200,
                "description": "item1",
                "additional": {
                    "length": 10,
                    "height": 10,
                    "breadth": 10,
                    "weight": 100,
                    "images": "http://sample-file1.jpg,http://sample-file2.jpg"
                },
                "quantity": 1,
                "sku": "XYZ1"
            }
        ],
        "cod_value": 200,
        "courier_partner": 3
    }
}
```
The create order API allows uploading the package details (manifest information) into the courier partner’s system and returns a label generated by them. You can create single order; errors/warnings will be highlighted in the response.

Please note, in case of any validation failure - order will not get created. Please wait for 8 seconds before you reject a rest-request for latency.

Async flag in additional object allows users to choose if order need to be generated in real time or in background. For bulk order creation async=true is recommended. Orders data in case of async is provided via webhooks.

The API is a HTTP POST request to: `https://www.clickpost.in/api/v3/create-order/` where output format is json.

Listed below are the parameters:
####URL parameters:
Parameter | Type | Description
--------- | ---- | -----------
username | character | User name provided to you
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
tin | character | TIN number of seller (Now GST No)
images | character | comma separated images of the item
#####GST Information
Parameter | Type | Description
--------- | ---- | -----------
enterprise_gstin | string | GST No of enterprise shipping the shipment
seller_gstin | string | GST No of seller sending the shipment (will be different from above for marketplaces)
taxable_value | double | taxable amount for GST (generally invoice_value of shipment)
ewaybill_serial_number | string | ewaybill for the shipment (optional)
is_seller_registered_under_gst | boolean | True / False, depending on whether you are registered for GST
place_of_supply | string | place of supply of service/product (https://cleartax.in/s/gst-state-code-jurisdiction)
gst_discount | double | discount given under gst, if any (optional)
hsn_code | string | HSN code for the product shipped (You may search for HSN https://cleartax.in/s/gst-hsn-lookup)
gst_total_tax | double | total GST applicable for the shipment
sgst_tax_rate | integer | tax percent applicable for sgst for the shipment (optional)
sgst_amount | double | amount applicable for sgst for the shipment (optional)
igst_tax_rate | integer | tax percent applicable for igst for the shipment (optional)
igst_amount | double | amount applicable for igst for the shipment (optional)
cgst_tax_rate | integer | tax percent applicable for cgst for the shipment (optional)
cgst_amount | double | amount applicable for cgst for the shipment (optional)
consignee_gstin | string | GST No of consignee (compulsory for B2B shipments) 
invoice_reference | string | invoice number for the shipment
#####Order type:
Parameter | Type | Description
--------- | ---- | -----------
order_type | character | COD/PREPAID/EXCHANGE
cod_value | double | if order_type = COD, cod_value should be greater than 0, if order_type = PREPAID, cod_value should be equal to 0
#####Courier Partner:
Parameter | Type | Description
--------- | ---- | -----------
courier_partner | integer | ID of courier partner for which the order is to be placed.
account_code | character | (optional) in case you have multiple accounts for a courier partner, code of account saved in clickpost is to be passed in additional object

List of courier partners is present at:
<a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>

#####**additional object:**
Parameter | Type | Description
--------- | ---- | -----------
label | boolean | true or false based upon if label need to be generated
return_info | object | return info object information if needed
awb_number | character | awb number if available
delivery_type | character| FORWARD or RVP
rvp_reason | character | rvp reason if order is for reverse pickup
priority | character| "NORMAL" or any other priority for order
async | boolean| for real time orders false and true if order need to generated in background
gst_number | character| gst number for tax purposes

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

##Order Creation Multi Model API
> URL to hit:

```
https://www.clickpost.in/api/v3/create-order/?username=<user-name>&key=<api-key>
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```
> __Example:__ POST Body

```json
{
    "pickup_info": {
        "email": "mrigendrasinha@gmail.com",
        "pickup_name": "Test Pickup Name",
        "pickup_phone": "8080808080",
        "pickup_address": "No.5, Pycroft Garden Road, Mohammed Sathak Trust, 5th Floor, Nungambakkam",
        "pickup_pincode": "110016",
        "pickup_city": "DELHI",
        "pickup_state": "TAMILNADU",
        "pickup_country": "IN",
        "pickup_time": "2017-11-15T09:25:00.000Z",
        "tin": "33030721658"
    },
    "drop_info": {
        "drop_name": "Test Drop Name",
        "drop_phone": "8080808080",
        "drop_address": "No.5, Pycroft Garden Road, Mohammed Sathak Trust, 5th Floor, Nungambakkam",
        "drop_pincode": "223045",
        "drop_city": "BANGLORE",
        "drop_state": "TAMILNADU",
        "drop_country": "IN"
    },
    "shipment_details": {
        "courier_partner": 5,
        "height": 1,
        "length": 1,
        "breadth": 1,
        "weight": 10,
        "reference_number": "RE1234",
        "order_type": "PREPAID",
        "cod_value": 0,
        "items": [{
            "price": 1000,
            "description": "dfdsfsd",
            "sku": "asasa",
            "quantity": 1,
            "weight": 1
        }],
        "invoice_number": "INV123",
        "invoice_value": 1000,
        "invoice_date": "2017-11-11"
    },
    "gst_info": {
        "seller_gstin": "1234",
        "taxable_value": 100,
        "ewaybill_serial_number": "2345677",
        "is_seller_registered_under_gst": false,
        "sgst_tax_rate": 100,
        "place_of_supply": "DELHI",
        "gst_discount": 0,
        "hsn_code": "1234",
        "sgst_amount": 100,
        "enterprise_gstin": "13",
        "gst_total_tax": 100,
        "igst_amount": 100,
        "cgst_amount": 200,
        "gst_tax_base": 200,
        "consignee_gstin": "1233",
        "igst_tax_rate": 100,
        "invoice_reference": "1234",
        "cgst_tax_rate": 100
    },
    "additional": {
        "data_validation": true,
        "label": true,
        "multi_modal": {
            "last_mile_courier_partner": 5,
            "last_mile_pickup_time": "2017-11-15 2:56 PM",
            "last_mile_order_type": "PREPAID",
            "transit_info": {
                "transit_city": "CHANDIGARH",
                "transit_state": "CHANDIGARH",
                "transit_phone": "8080808080",
                "transit_name": "Mr.Arun",
                "transit_pincode": "160017",
                "transit_address": "229A, 2nd Floor, Elante Mall, Industrial Area,Phase-1",
                "transit_country": "IN",
                "transit_email": "a@a.com"
            }
        }
    }
}
```

> __Response__

```
{
    "order_id": 76703,
    "meta": {
        "status": 200,
        "success": true,
        "message": "Order Placed Successfully"
    },
    "result": {
        "reference_number": "RE1234",
        "DestinationArea": "CAR",
        "waybill": "69573426016",
        "label1": "https://pyck-res-bucket.s3.amazonaws.com:443/bluedart/2017-11-30/69573426016.pdf",
        "waybill1": "69573426016",
        "label": "https://pyck-res-bucket.s3.amazonaws.com:443/bluedart/2017-11-30/69573426016.pdf",
        "DestinationLocation": "CMM"
    },
    "tracking_id": 3475042
}
```

The create order Multi Model API allows uploading the package details (manifest information) into the courier partner’s system for multi hop shipment (2 courier company do the delivery of shipment) and returns a label generated by them. You can create single order; errors/warnings will be highlighted in the response.

Please note, in case of any validation failure - order will not get created. Please wait for 8 seconds before you reject a rest-request for latency.

The API is a HTTP POST request to: `https://www.clickpost.in/api/v3/create-order/` where output format is json.

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
tin | character | TIN number of seller (Now GST No)
#####GST Information
Parameter | Type | Description
--------- | ---- | -----------
enterprise_gstin | string | GST No of enterprise shipping the shipment
seller_gstin | string | GST No of seller sending the shipment (will be different from above for marketplaces)
taxable_value | double | taxable amount for GST (generally invoice_value of shipment)
ewaybill_serial_number | string | ewaybill for the shipment (optional)
is_seller_registered_under_gst | boolean | True / False, depending on whether you are registered for GST
place_of_supply | string | place of supply of service/product (https://cleartax.in/s/gst-state-code-jurisdiction)
gst_discount | double | discount given under gst, if any (optional)
hsn_code | string | HSN code for the product shipped (You may search for HSN https://cleartax.in/s/gst-hsn-lookup)
gst_total_tax | double | total GST applicable for the shipment
sgst_tax_rate | integer | tax percent applicable for sgst for the shipment (optional)
sgst_amount | double | amount applicable for sgst for the shipment (optional)
igst_tax_rate | integer | tax percent applicable for igst for the shipment (optional)
igst_amount | double | amount applicable for igst for the shipment (optional)
cgst_tax_rate | integer | tax percent applicable for cgst for the shipment (optional)
cgst_amount | double | amount applicable for cgst for the shipment (optional)
consignee_gstin | string | GST No of consignee (compulsory for B2B shipments) 
invoice_reference | string | invoice number for the shipment
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

#####**Compulsory fields in additional object:**
Parameter | Type | Description
--------- | ---- | -----------
label | boolean | true or false based upon if label need to be generated
rvp_reason | character | rvp reason if order is for reverse pickup
priority | character| "NORMAL" or any other priority for order
return_info | object | return info object information if needed
awb_number | character | awb number if available
delivery_type | character| FORWARD or any other order type
async | boolean| for real time orders false and true if order need to generated in background
gst_number | character| gst number for tax purposes

#####**Transit address detail need to be passed in additional object:**
Parameter | Type | Description
--------- | ---- | -----------
last_mile_courier_partner | int | courier company id provided by us
last_mile_pickup_time | timestamp | pick up time for in transit hop (for last mile courier company)
last_mile_order_type | character | order type cod or prepaid for last mile
transit_city | character | transit city from where last mile pick the order for delivery
transit_state | character | transit state from where last mile pick the order for delivery
transit_phone | int | transit phone no
transit_name | character | person name from whol last mile picks the order
transit_pincode | int | pin code of location for last mile to pick
transit_address | character | address for last mile courier company to pick the order
transit_country | character | country code for the address
transit_email | character | email id for reference to pick order for last mile

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
  6. waybill1: another waybill generated by courier partner for the shipment
  7. label1: Another AWS link of the label generated for the shipment (Not generated for RVP shipments)

##Order Creation B2B API
> URL to hit:

```
https://www.clickpost.in/api/v1/create-order/?username=<user-name>&key=<api-key>
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```
> __Example:__ POST Body

```json
{
    "breadth": 10,
    "drop_name": "Rahul",
    "order_type": "PREPAID",
    "invoice_date": "2015-12-27",
    "priority": "NORMAL",
    "pickup_pincode": "110008",
    "drop_city": "DELHI",
    "reference_number": "ad123",
    "drop_address": "L-19B, third Floor Malviya Nagar, New Delhi",
    "courier_partner": 1,
    "gst_info": {
        "is_seller_registered_under_gst": false,
        "place_of_supply": "DELHI",
        "invoice_reference": "1234",
        "gst_tax_base": 200,
        "hsn_code": "1234",
        "gst_discount": 0,
        "sgst_tax_rate": 100,
        "igst_amount": 100,
        "taxable_value": 100,
        "sgst_amount": 100,
        "seller_gstin": "1234",
        "gst_total_tax": 100,
        "ewaybill_serial_number": "2345677",
        "consignee_gstin ": "1233",
        "enterprise_gstin": "13",
        "igst_tax_rate": 100,
        "cgst_amount": 200,
        "cgst_tax_rate": 100
    },
    "tin": "120349483",
    "email": "founders@clickpost.in",
    "return_info": {
        "state": "DELHI",
        "country": "IN",
        "city": "DELHI",
        "phone": 8080808080,
        "name": "Deepanshu",
        "pincode": "110019",
        "address": "Test Address top floor Nehru Place New Delhi "
    },
    "pickup_phone": "8080808080",
    "drop_state": "DELHI",
    "pickup_time": "2017-11-23T12:00:00Z",
    "pickup_state": "Haryana",
    "drop_pincode": "110017",
    "drop_country": "IN",
    "weight": 100,
    "length": 10,
    "invoice_value": 1000,
    "height": 10,
    "drop_phone": "8080808080",
    "pickup_name": "Deepanshu",
    "awb_number": "553889122",
    "data_validation": false,
    "pickup_country": "IN",
    "invoice_number": "INV-234/3",
    "pickup_address": "A-228 top floor near XYZ, Gurgaon",
    "pickup_city": "Gurgaon",
    "cod_value": 0,
    "shipment_type": "MPS",
    "items": [{
        "length": 10,
        "breadth": 15,
        "sku": "XYZ1",
        "price": 200,
        "height": 17,
        "weight": 100,
        "description": "bottle",
        "quantity": 1
    }]
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
        "label": "https://pyck-res-bucket.s3.amazonaws.com:443/fedex/2017-02-11/785578015860.pdf",
        "children": [{
                "reference_number": "ASDF1234",
                "waybill": "785578015860_1",
                "label": null,
                "item": {
                    "height": 10,
                    "quantity": 1,
                    "price": 200,
                    "breadth": 10,
                    "description": "item1",
                    "weight": 100,
                    "waybill": "58402429105_1",
                    "sku": "XYZ1",
                    "length": 10
                }
            },
            {
                "reference_number": "ASDF1234",
                "waybill": "785578015860_2",
                "label": null,
                "item": {
                    "height": 10,
                    "quantity": 1,
                    "price": 200,
                    "breadth": 10,
                    "description": "item2",
                    "weight": 100,
                    "waybill": "58402429105_1",
                    "sku": "XYZ2",
                    "length": 10
                }
            }
        ]
    }
}
```

The create order B2B API allows uploading the package details (manifest information) for multi piece shipment into the courier partner’s system and returns a label generated by them. You can create single order; errors/warnings will be highlighted in the response.

Details for multiple shipments needs to passed in items array during object creation. This array is treated as multiple shipments if shipment_type is MPS.

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
shipment_type | character | MPS (Compulsory)
#####GST Information
Parameter | Type | Description
--------- | ---- | -----------
enterprise_gstin | string | GST No of enterprise shipping the shipment
seller_gstin | string | GST No of seller sending the shipment (will be different from above for marketplaces)
taxable_value | double | taxable amount for GST (generally invoice_value of shipment)
ewaybill_serial_number | string | ewaybill for the shipment (optional)
is_seller_registered_under_gst | boolean | True / False, depending on whether you are registered for GST
place_of_supply | string | place of supply of service/product (https://cleartax.in/s/gst-state-code-jurisdiction)
gst_discount | double | discount given under gst, if any (optional)
hsn_code | string | HSN code for the product shipped (You may search for HSN https://cleartax.in/s/gst-hsn-lookup)
gst_total_tax | double | total GST applicable for the shipment
sgst_tax_rate | integer | tax percent applicable for sgst for the shipment (optional)
sgst_amount | double | amount applicable for sgst for the shipment (optional)
igst_tax_rate | integer | tax percent applicable for igst for the shipment (optional)
igst_amount | double | amount applicable for igst for the shipment (optional)
cgst_tax_rate | integer | tax percent applicable for cgst for the shipment (optional)
cgst_amount | double | amount applicable for cgst for the shipment (optional)
consignee_gstin | string | GST No of consignee (compulsory for B2B shipments) 
invoice_reference | string | invoice number for the shipment
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
  4. All above details will be given for children awbs as well under children field along with item info, which is an array having label, awb and reference number for all the children
  Additional fields for Bluedart:
  5. DestinationLocation: 3 digit destination location code needed by Bluedart on shipping label
  6. DestinationArea: 3 digit destination area code needed by Bluedart on shipping label


<aside class="warning">
You must replace Username/key with the username/key provided to you.
</aside>

----------
