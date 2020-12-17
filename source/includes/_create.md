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
  "items": [{"product_url":"<Product Page Url>", "price":"370.00","description":"IN1543MTOSKTBLA-146-10","sku":"IN1543MTOSKTBLA-146-10","quantity":"1","images": "http://sample-file1.jpg,http://sample-file2.jpg"},{"product_url":"<Product Page Url>","price":"694.00","description":"IN1516MTODREMLT-147-10","sku":"IN1516MTODREMLT-147-10","quantity":"1","images": "http://sample-file1.jpg,http://sample-file2.jpg"}],
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

```json
{
  "meta": {
    "message": "Order Placed Successfully",
    "status": 200,
    "success": true
  },
  "result": {
    "reference_number": "SAMPLE-REF-No",
    "waybill": "785578015860",
    "label": "https://pyck-res-bucket.s3.amazonaws.com:443/fedex/2017-02-11/785578015860.pdf",
    "security_key": "560fee51-1af3-4d1d-a6e8-0149b0868d38",
    "sort_code": "ABC/HYG/TEX/LUV"
  }
}
```

> __Example:__ POST Body (PREPAID Shipment)

```json
{
    "pickup_address": "B-220/2, 1st Floor, Right Door, Savitri Nagar, New Delhi",
    "pickup_city": "DELHI",
    "pickup_state": "DELHI",
    "pickup_country": "IN",
    "pickup_pincode": "110017",
    "pickup_time": "2015-12-10T12:00:00Z",
    "drop_name": "Rahul",
    "drop_phone": "8376035546",
    "drop_address": "L-19B, Third Floor, Malviya Nagar, New Delhi",
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
    "items": [{"product_url":"<Product Page Url>","price":"370.00","description":"IN1543MTOSKTBLA-146-10","sku":"IN1543MTOSKTBLA-146-10","quantity":"1","images": "http://sample-file1.jpg,http://sample-file2.jpg"},{"product_url":"<Product Page Url>","price":"694.00","description":"IN1516MTODREMLT-147-10","sku":"IN1516MTODREMLT-147-10","quantity":"1","images":"http://sample-file1.jpg,http://sample-file2.jpg"}],
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

```json
{
    "courier_partner": 7,
    "email": "founders@clickpost.in",
    "pickup_name": "Deepanshu",
    "pickup_phone": "8080808080",
    "pickup_address": "B-220/2, 1st Floor, Right Door, Savitri Nagar, New Delhi",
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
    "items": [{"product_url":"<Product Page Url>", "price": 200, "description": "item1", "sku":
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

```json
{
    "courier_partner": 7,
    "email": "founders@clickpost.in",
    "pickup_name": "Deepanshu",
    "pickup_phone": "8080808080",
    "pickup_address": "B-220/2, 1st Floor, Right Door, Savitri Nagar, New Delhi",
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
    {"product_url":"<Product Page Url>",
    "price": 200, 
    "description": "item1",
    "sku": "XYZ1",
    "quantity": 1,
    "cat": "electronics",
    "sub_cat": "tv",
    "color": "Red",
    "serial_no": "SRN1237890000",
    "size": "7",
    "qc_rules": [
    {
        "question": "Is product colour as per description ?",
        "is_mandatory": 1,
        "value": "Red"
    },
    {
        "question": "Is product size as per description ?",
        "is_mandatory": 1,
        "value": "7"
      }
    ],
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
    "qc_type": "doorstep",
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
items | List | Json list with multiple item objects in it. Each item object should have following:
price | double | price of the item
description | character | Item description
sku | character | SKU unit name of item
quantity | Integer | number of item pieces
product_url |  string | url of the product on the website
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

#####Optional field for RVP (Doorstep QC):
Parameter | Type | Description
--------- | ---- | -----------
qc_type | character | pass "doorstep" if you want reverse pickup to be done as doorstep quality check as leave it blank
image_urls | character | add this field in items array for each item. value will be comma seperated url strings without spaces.
cat | character | category of product for qc questions to be asked at doorstep. To be passed in items array for each item object (only for shadowfax reverse with qc_type: doorstep)
sub_cat | character | sub category of product for qc questions to be asked at doorstep. To be passed in items array for each item object (only for shadowfax reverse with qc_type: doorstep)
color | character | color of the item to be picked (only for shadowfax reverse with qc_type: doorstep)
serial_no | character | serial_no of the item to be picked (only for shadowfax reverse with qc_type: doorstep)
size | character | size of the item to be picked (only for shadowfax reverse with qc_type: doorstep)
qc_rules | json array | questions to be asked by pickup boy (only for shadowfax reverse with qc_type: doorstep)

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
  4. security_key: All orders are allocated a security key, please store this security key in your system (36 char)
  5. sort_code: for certain logistics partners, a sort_code is passed in API response that you can consume if you generate the shipping label at your end. For courier partners where this is not needed, it will have null value (max 20 char)
  Additional fields for Bluedart:
  6. DestinationLocation: 3 digit destination location code needed by Bluedart on shipping label
  7. DestinationArea: 3 digit destination area code needed by Bluedart on shipping label

##Order Creation V3 API (Forward)
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
        "pickup_phone": "9816691388",
        "pickup_lat": "10.01",
        "pickup_long": "10.00"
    },
    "drop_info": {
        "drop_address": "F-68 third floor kalkaji New Delhi ",
        "drop_phone": "9717732407",
        "drop_country": "IN",
        "drop_state": "DELHI",
        "drop_pincode": "110019",
        "drop_city": "Delhi",
        "drop_name": "Prashant",
        "drop_email": "support@clickpost.in",
        "drop_lat": "10.01",
        "drop_long": "10.00"
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
                "product_url":"<Product Page Url>",
                "price": 200,
                "description": "item1",
                "quantity": 1,
                "sku": "XYZ1",
                "additional": {
                    "length": 10,
                    "height": 10,
                    "breadth": 10,
                    "weight": 100,
                    "images": "http://sample-file1.jpg,http://sample-file2.jpg",
                    "return_days": 2
                }
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
        "reseller_info": {
            "name": "Clickpost Support",
            "phone": "8080808080"
        },
        "awb_number": "43062728295",
        "delivery_type": "FORWARD",
        "async": false,
        "gst_number" : "21313",
        "account_code": "<account_code generated via clickpost dashboard>",
        "from_wh": "From Warehouse",
        "to_wh": "To Warehouse",
        "channel_name": "Channel Name: In case you have different channels to receive orders",
        "order_date": "YYYY-MM-DD",
        "enable_whatsapp": false, # Useful for whatsapp communication
        "is_fragile": true,
        "is_dangerous": true,
        "order_id": "Order ID of the shipment"
    }
}
```

> __Response__

```json
{
  "meta": {
    "message": "Order Placed Successfully",
    "status": 200,
    "success": true
  },
  "result": {
    "courier_partner_id": 1,
    "courier_name": "Fedex",
    "sort_code": null,
    "security_key": "560fee51-1af3-4d1d-a6e8-0149b0868d38",
    "reference_number": "ASDF1234",
    "waybill": "785578015860",
    "label": "https://pyck-res-bucket.s3.amazonaws.com:443/fedex/2017-02-11/785578015860.pdf"
  }
}
```

> __Example:__ POST Body (PREPAID Shipment)

```json
{
    "pickup_info": {
        "pickup_state": "DELHI",
        "pickup_address": "A-228 top floor kalkaji New Delhi ",
        "email": "support@clickpost.in",
        "pickup_time": "2017-05-20T12:00:00Z",
        "pickup_pincode": "110019",
        "pickup_city": "DELHI",
        "tin": "120349483",
        "pickup_name": "Deepanshu",
        "pickup_country": "IN",
        "pickup_phone": "8080808080",
        "pickup_lat": "10.01",
        "pickup_long": "10.00"

    },
    "drop_info": {
        "drop_address": "F-68 third floor kalkaji New Delhi ",
        "drop_phone": "8080808080",
        "drop_country": "IN",
        "drop_state": "DELHI",
        "drop_pincode": "110019",
        "drop_city": "Delhi",
        "drop_name": "Prashant",
        "drop_email": "support@clickpost.in",
        "drop_lat": "10.01",
        "drop_long": "10.00"
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
                "product_url":"<Product Page Url>",
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
        "cod_value": 0,
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
        "label ": true,
        "return_info": {
            "pincode": "110019",
            "address": "Test Address top floor kalkaji New Delhi ",
            "state": "DELHI",
            "phone": "8080808080",
            "name": "Deepanshu",
            "city": "DELHI",
            "country": "IN"
        },
        "awb_number": "43062728295",
        "delivery_type": "FORWARD",
        "async": false,
        "gst_number" : "21313",
        "account_code": "ecom surface",
        "from_wh": "From Warehouse",
        "to_wh": "To Warehouse",
        "channel_name": "Channel Name: In case you have different channels to receive orders",
        "order_date": "YYYY-MM-DD",
        "is_fragile": true,
        "is_dangerous": true,
        "order_id": "order ID of the shipment"
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
pickup_phone | character | 10/11 digit phone number
pickup_pincode | character | 6 digit pincode
pickup_address | character | maximum length of 500 characters
pickup_time | character | (ISO Format: example 2015-12-10T12:00:00Z)
pickup_city | character | pickup city name, maximum length 200 characters
pickup_state | character | pickup state name, maximum length 200 characters
pickup_country | character | pickup country name, maximum length 100 characters 
email | character | email id to be sent to courier partner for this shipment
tin | character | Seller TIN if available. If not, please pass GST No here
pickup_lat | character | [optional] latitude of pickup location, required for Hyperlocal courier partners 
pickup_long | character | [optional] longitude of pickup location, required for Hyperlocal courier partners 

#####Drop Information
Parameter | Type | Description
--------- | ---- | -----------
drop_name | character | maximum length of 100 characters
drop_address | character | maximum length of 500 characters
drop_phone | character | 10/11 digit phone number
drop_pincode | character | 6 digit pincode
drop_city | character | drop city name, maximum length 200 characters
drop_state | character | drop state name, maximum length 200 characters
drop_country | character | drop country name, maximum length 200 characters
drop_email | character | email of the customer
drop_lat | character | [optional] latitude of drop location, required for Hyperlocal courier partners 
drop_long | character | [optional] longitude of drop location, required for Hyperlocal courier partners 


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
items | List | Json list with multiple item objects in it. Each item object should have following:
price | double | price of the item
description | character | Item description
sku | character | SKU unit name of item
quantity | Integer | number of item pieces (should be always > 0)
product_url | character | product page url for the item on website
invoice_value | decimal/float/integer | value
invoice_number | character | string of length 50 characters
invoice_date | character | Format: YYYY-MM-DD, example: 2015-12-25 for 25th December 2015
reference_number | character | reference number to tag the order with your order id.
length | integer | length of shipment in cm
breadth | integer | breadth of shipment in cm
height | integer | height of shipment in cm
weight | integer | weight of shipment in grams
tin | character | TIN number of seller (Now GST No)
images | character | comma separated images of the item

#####Order type:
Parameter | Type | Description
--------- | ---- | -----------
order_type | character | COD/PREPAID/EXCHANGE, to be passed in shipment_details object
cod_value | double | if order_type = COD, cod_value should be greater than 0, if order_type = PREPAID, cod_value should be equal to 0. To be passed in shipment_details object

#####Courier Partner:
Parameter | Type | Description
--------- | ---- | -----------
courier_partner | integer | ID of courier partner for which the order is to be placed. This is to be passed in shipment_details object
account_code | character | (optional) in case you have multiple accounts for a courier partner in Clickpost, code of account saved in clickpost is to be passed in additional object

List of courier partners is present at:
<a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>

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

#####additional object
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
pickup_type | character | Acceptable values: "WH" (for warehouse pickup) / "SL" (for seller pickup [marketplace]). This value is passed to EcomExpress only
vendor_code | character | (optional) vendor code of pickup location. If this field is not provided, Clickpost will generate vendor code for the pickup location. For Ecom Express this field is passed to them as "pickup_location_code" to create location tagging. For Delhivery this field is passed in the API field 'pickup_location["name"]'. For XpressBees, this field is passed in their API field "PickupVendorCode".
is_fragile | boolean | true if shipment is fragile. Default false. [Currently used only for eKart and delhivery APIs]
is_dangerous | boolean | true if shipment is dangerous/liquid. Default false. [Currently used only for eKart and delhivery APIs]
order_id | character [50 characters] | order ID of the shipment


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
      - 400 if there is a bad request encountered: errors will be present in "message"
2. result:
  1. reference_number: reference number provided in the post data
  2. waybill: waybill generated by courier partner for the shipment
  3. label: AWS link of the label generated for the shipment (Not generated for RVP shipments)
  4. sort_code: Sort Code of shipment, needed by certain logistics partner on the label. response will be null if the sort code is not applicable for logistics partner. Right now populated for Delhivery / Ecom / Bluedart / XpressBees. (max 20 char)
  5. security_key: All orders are allocated a security key, please store this security key in your system (36 char)
  6. courier_partner_id: Clickpost courier partner ID for the order for which the AWB was generated
  7. courier_name: Name of courier. For aggregators like Shiprocket, this field will have the courier name on which Shiprocket generated the label


##Order Creation V3 API (Reverse)
```
https://www.clickpost.in/api/v3/create-order/?username=<user-name>&key=<api-key>
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```
> __Example:__ POST Body

```json
{
    "pickup_info": {
        "pickup_state": "DELHI",
        "pickup_address": "A-228 top floor kalkaji New Delhi ",
        "email": "support@clickpost.in",
        "pickup_time": "2017-05-20T12:00:00Z",
        "pickup_pincode": "110019",
        "pickup_city": "DELHI",
        "tin": "120349483",
        "pickup_name": "Deepanshu",
        "pickup_country": "IN",
        "pickup_phone": "8080808080",
        "pickup_lat": "10.01",
        "pickup_long": "10.00"
    },
    "drop_info": {
        "drop_address": "F-68 third floor kalkaji New Delhi ",
        "drop_phone": "8080808080",
        "drop_country": "IN",
        "drop_state": "DELHI",
        "drop_pincode": "110019",
        "drop_city": "Delhi",
        "drop_name": "Prashant",
        "drop_email": "support@clickpost.in",
        "drop_lat": "10.01",
        "drop_long": "10.00"
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
                "product_url":"<Product Page Url>",
                "price": 200,
                "description": "item1",
                "quantity": 1,
                "sku": "XYZ1",
                "image_urls": [
                    "https://assetscdn.paytm.com/images/catalog/view_item/114560/123.jpg",
                    "https://assetscdn.paytm.com/images/catalog/view_item/116303/123434.jpg"
                ],
                "cat": "electronics",
                "sub_cat": "tv",
                "color": "Red",
                "serial_no": "SRN1237890000",
                "size": "7",
                "qc_rules": [{
                    "question": "Is product colour as per description ?",
                    "is_mandatory": 1,
                    "value": "Red"
                },
                {
                    "question": "Is product size as per description ?",
                    "is_mandatory": 1,
                    "value": "7"
                }],
                "additional": {
                    "length": 10,
                    "height": 10,
                    "breadth": 10,
                    "weight": 100
                }
            }
        ],
        "cod_value": 0,
        "courier_partner": 24
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
        "label ": true,
        "awb_number": "43062728295",
        "delivery_type": "RVP",
        "rvp_reason": "Shipper cancellation",
        "qc_type": "doorstep",
        "async": false,
        "account_code": "ecom reverse",
        "from_wh": "From Warehouse",
        "to_wh": "To Warehouse",
        "channel_name": "Channel Name: In case you have different channels to receive orders",
        "order_date": "YYYY-MM-DD",
        "order_id": "order ID of the shipment"
    }
}
```

1. All parameter definition remains same as manifestation v3 Forward API
2. Following parameters are the changes in manifestation v3 Forward API:

#####**Compulsory fields for RVP order creation:**
Parameter | Type | Description
--------- | ---- | -----------
rvp_reason | character | stating the reason for Reverse Pickup
delivery_type | character | For Reverse Pickup, the value of this field should  be **"RVP"**

#####Optional field for RVP (Doorstep QC):
Parameter | Type | Description
--------- | ---- | -----------
qc_type | character | pass "doorstep" if you want reverse pickup to be done as doorstep quality check as leave it blank
image_urls | character | add this field in items array for each item. value will be comma seperated url strings without spaces.
cat | character | category of product for qc questions to be asked at doorstep. To be passed in items array for each item object (only for shadowfax reverse with qc_type: doorstep)
sub_cat | character | sub category of product for qc questions to be asked at doorstep. To be passed in items array for each item object (only for shadowfax reverse with qc_type: doorstep)
color | character | color of the item to be picked (only for shadowfax reverse with qc_type: doorstep)
serial_no | character | serial_no of the item to be picked (only for shadowfax reverse with qc_type: doorstep)
size | character | size of the item to be picked (only for shadowfax reverse with qc_type: doorstep)
qc_rules | json array | questions to be asked by pickup boy (only for shadowfax reverse with qc_type: doorstep)

If you want to pass above parameters as QC for other reverse logistics partners, please contact support@clickpost.in for integrations request.

##Multiseller items shipment API

```
https://www.clickpost.in/api/v3/create-order/?username=<user-name>&key=<api-key>
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```
> __Example:__ POST Body

```json
{
    "pickup_info": {
        "pickup_time": "2017-09-20T12:00:00Z",
        "email": "pankaj@khazanabazaar.com",
        "pickup_address": "402, Orbit tower, Sahara Darwaja, Ring Road, Surat - 395002",
        "pickup_state": "GUJARAT",
        "pickup_name": "Pankaj Kubadiya",
        "pickup_country": "IN",
        "tin": "120349483",
        "pickup_city": "SURAT",
        "pickup_phone": "08469591430",
        "pickup_pincode": "395002"
    },
    "drop_info": {
        "drop_country": "IN",
        "drop_city": "Delhi",
        "drop_phone": "9717732402",
        "drop_address": "F-68 third floor kalkaji New Delhi ",
        "drop_name": "Prashant",
        "drop_state": "DELHI",
        "drop_pincode": "110019",
        "drop_email": "support@clickpost.in"
    },
    "shipment_details": {
        "breadth": 10,
        "cod_value": 200,
        "height": 12,
        "invoice_date": "2015-12-27",
        "length": 10,
        "order_type": "COD",
        "invoice_number": "INV123",
        "invoice_value": 200,
        "items": [{
            "quantity": 1,
            "sku": "XYZ1",
            "price": 200,
            "description": "item1",
            "gst_info": {
                "consignee_gstin": "1233",
                "invoice_reference": "1234",
                "seller_gstin": "1234",
                "cgst_tax_rate": 100,
                "place_of_supply": "DELHI",
                "sgst_tax_rate": 100,
                "igst_tax_rate": 100,
                "enterprise_gstin": "13",
                "gst_tax_base": 200,
                "igst_amount": 100,
                "is_seller_registered_under_gst": false,
                "sgst_amount": 100,
                "taxable_value": 100,
                "gst_discount": 0,
                "gst_total_tax": 100,
                "hsn_code": "1234",
                "ewaybill_serial_number": "2345677",
                "cgst_amount": 200,
                "invoice_value": 200,
                "seller_name": "Deepanshu",
                "seller_address": "A-228 top floor kalkaji",
                "seller_state": "Delhi",
                "seller_pincode": "110019",
                "invoice_number": "1882782",
                "invoice_date": "2018-08-23"
            },
            "additional": {
                "breadth": 10,
                "product_url":"<Product Page Url>",
                "images": "http://sample-file1.jpg,http://sample-file2.jpg",
                "length": 10,
                "weight": 100,
                "height": 10
            }
        }],
        "courier_partner": 3,
        "weight": 100,
        "reference_number": "UNIQUE-SHIPMENT-ID"
    },
    "additional": {
        "label": true,
        "data_validation": true,
        "async": false,
        "return_info": {
            "email": "support@clickpost.in",
            "name": "Deepanshu",
            "phone": "8080808080",
            "address": "Test Address top floor Kalkaji New Delhi ",
            "country": "IN",
            "city": "DELHI",
            "pincode": "110019",
            "state": "DELHI"
        },
        "delivery_type": "FORWARD",
        "vendor_code": "<WH_CODE>",
        "pickup_type": "WH",
        "is_multi_seller": true,
        "from_wh": "From Warehouse",
        "to_wh": "To Warehouse",
        "channel_name": "Channel Name: In case you have different channels to receive orders",
        "order_date": "YYYY-MM-DD",
        "order_id": "order ID of the shipment",
        "enable_whatsapp": false # Useful for whatsapp communication 
    }
}
```
> __Response__

```json
{
  "meta": {
    "message": "Order Placed Successfully",
    "status": 200,
    "success": true
  },
  "result": {
    "sort_code": "DEL/SET",
    "security_key": "560fee51-1af3-4d1d-a6e8-0149b0868d38",
    "reference_number": "UNIQUE-SHIPMENT-ID",
    "waybill": "785578015860",
    "label": "https://pyck-res-bucket.s3.amazonaws.com:443/ECOM/2017-02-18/785578015860.pdf"
  }
}
```

The create order Multi Seller shipment API allows uploading the package details (manifest information) into the courier partner’s system for single shipment having multiple items in it (having different GST values) and returns a label generated by them. You can create single order; errors/warnings will be highlighted in the response.

Please note, in case of any validation failure - order will not get created. Please wait for 8 seconds before you reject a rest-request for latency.

The API is a HTTP POST request to: `https://www.clickpost.in/api/v3/create-order/` where output format is json.

All the parameters are same as manifestation v3 API. Changes are:

1. gst_info added in shipment_details object
2. is_multi_seller: true flag to be passed in the additional object.


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
        "drop_country": "IN",
        "drop_email": "support@clickpost.in"
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
            "product_url":"<Product Page Url>",
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

```json
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
items | List | Json list with multiple item objects in it. Each item object should have following:
price | double | price of the item
description | character | Item description
sku | character | SKU unit name of item
quantity | Integer | number of item pieces
product_url | character | item url on website 
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
https://www.clickpost.in/api/v3/create-order/?username=<user-name>&key=<api-key>
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```
> __Example:__ POST Body

```json
{
    "pickup_info": {
        "pickup_time": "2018-11-20T12:00:00Z",
        "email": "support@clickpost.in",
        "pickup_address": "Test Pickup Warehouse Address, Pickup Locality, Surat - 395002",
        "pickup_state": "GUJARAT",
        "pickup_name": "Test Pickup Warehouse Name",
        "pickup_country": "IN",
        "tin": "<GST_NUMBER>",
        "pickup_city": "SURAT",
        "pickup_phone": "8080808080",
        "pickup_pincode": "395002"
    },
    "drop_info": {
        "drop_country": "IN",
        "drop_city": "Delhi",
        "drop_phone": "8080808080",
        "drop_address": "Test Drop address, Drop Locality, New Delhi ",
        "drop_name": "Test Drop Name",
        "drop_state": "DELHI",
        "drop_pincode": "110020",
        "drop_email": "support@clickpost.in"
    },
    "shipment_details": {
        "breadth": 10, 
        "cod_value": 300,
        "height": 12,
        "invoice_date": "2018-11-12",
        "length": 10,
        "order_type": "COD",
        "invoice_number": "INV123",
        "invoice_value": 200,
        "shipment_type": "MPS",
        # Each item in items object represent a carton box.
        "items": [{
            "quantity": 1,
            "sku": "XYZ1",
            "price": 200,
            "description": "Cartoon Box 1",
            "gst_info": {
                "consignee_gstin": "11ANKPT8882D1ZD",
                "invoice_reference": "DC68HJJ",
                "seller_gstin": "11ANKPT8882D1ZC",
                "cgst_tax_rate": 100,
                "place_of_supply": "DELHI",
                "sgst_tax_rate": 100,
                "igst_tax_rate": 100,
                "enterprise_gstin": "13",
                "gst_tax_base": 200,
                "igst_amount": 100,
                "is_seller_registered_under_gst": false,
                "sgst_amount": 100,
                "taxable_value": 100,
                "gst_discount": 0,
                "gst_total_tax": 100,
                "hsn_code": "1234",
                "cgst_amount": 200,
                "invoice_value": 200,
                "seller_name": "Deepanshu",
                "seller_address": "A-228 top floor kalkaji",
                "seller_state": "Delhi",
                "seller_pincode": "110019",
                "invoice_number": "1882782",
                "invoice_date": "2018-08-23",
                "ewaybill_serial_number": "07AACCF1234T3AS",
                "ewaybill_expiry_date": "2018-12-31 18:58:56"
            },
            "additional": {
                "breadth": 10,
                "product_url":"<Product Page Url>",
                "images": "http://sample-file1.jpg,http://sample-file2.jpg",
                "length": 10,
                "weight": 100,
                "height": 10
            }
        },{
            "quantity": 1,
            "sku": "XYZ2",
            "price": 200,
            "description": "Cartoon Box 2",
            "gst_info": {
                "consignee_gstin": "11ANKPT8882D1ZD",
                "invoice_reference": "DC68HJJ1",
                "seller_gstin": "11ANKPT8882D1ZC",
                "cgst_tax_rate": 100,
                "place_of_supply": "DELHI",
                "sgst_tax_rate": 100,
                "igst_tax_rate": 100,
                "enterprise_gstin": "13",
                "gst_tax_base": 200,
                "igst_amount": 100,
                "is_seller_registered_under_gst": false,
                "sgst_amount": 100,
                "taxable_value": 100,
                "gst_discount": 0,
                "gst_total_tax": 100,
                "hsn_code": "1234",
                "cgst_amount": 200,
                "invoice_value": 200,
                "seller_name": "Deepanshu",
                "seller_address": "A-228 top floor kalkaji",
                "seller_state": "Delhi",
                "seller_pincode": "110019",
                "invoice_number": "1882783",
                "invoice_date": "2018-08-23"
            },
            "additional": {
                "breadth": 10,
                "product_url":"<Product Page Url>",
                "images": "http://sample-file1.jpg,http://sample-file2.jpg",
                "length": 10,
                "weight": 100,
                "height": 10
            }
        }],
        "courier_partner": 61,
        "weight": 200,
        "reference_number": "UNIQUE-SHIPMENT-ID7"
    },
    "additional": {
        "label": true,
        "data_validation": true,
        "async": false,
        "return_info": {
            "email": "support@clickpost.in",
            "name": "Test Return Warehouse Name",
            "phone": "8080808080",
            "address": "Test Return Address New Delhi ",
            "country": "IN",
            "city": "DELHI",
            "pincode": "110020",
            "state": "DELHI"
        },
        "delivery_type": "FORWARD",
        "vendor_code": "SBL",
        "pickup_type": "WH",
        "is_multi_seller": true,
        "account_code":"AIR",
        "from_wh": "From Warehouse",
        "to_wh": "To Warehouse",
        "channel_name": "Channel Name: In case you have different channels to receive orders",
        "order_id": "Order ID of the order"
    }
}
```

> __Response__

```json
{
    "meta": {
        "message": "Order Placed Successfully",
        "status": 200,
        "success": true
    },
    "result": {
        "security_key": "ee30803e-3fd9-460d-8cfa",
        "sort_code": "ABC/XYZ",
        "reference_number": "ASDF1234",
        "waybill": "785578015860",
        "label": "https://pyck-res-bucket.s3.amazonaws.com:443/XPRESBEES_CARGO/2017-02-11/785578015860.pdf",
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

Details for multiple shipments needs to passed in items array during object creation. This array is treated as multiple shipments/carton boxes if shipment_type is MPS.

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
items | List | Json list with multiple item objects in it. Each item object represents a carton and should have following:
price | double | price of the item
description | character | Item description
sku | character | SKU unit name of item
length | integer | in cm
breadth | integer | in cm
height | integer | in cm
weight | integer | grams
quantity | Integer | number of sku pieces
product_url | character | product page url on website, optional
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
  5. security_key: All orders are allocated a security key, please store this security key in your system (36 chars)
  6. sort_code: for certain logistics partners, a sort_code is passed in API response that you can consume if you generate the shipping label at your end. For courier partners where this is not needed, it will have null value (13 chars)
  Additional fields for Bluedart:
  7. DestinationLocation: 3 digit destination location code needed by Bluedart on shipping label
  8. DestinationArea: 3 digit destination area code needed by Bluedart on shipping label


<aside class="warning">
You must replace Username/key with the username/key provided to you.
</aside>

##Order Creation API [MENA, EU, US, SEA]

> URL to hit:

```
https://www.clickpost.in/api/v4/create-order/?username=<user-name>&key=<api-key>
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```
> __Example:__ POST Body

```json
{
    "pickup_info": {
        "city": "JK0701",
        "name": "www.stylishop.com",
        "time": "2020-02-01T10:53:33",
        "email": "hello.ksa@stylishop.com",
        "phone": "8001111090",
        "state": "Al-Riyadh",
        "address": "KRAMAT ASEM RAYA N0. 6, UTAN KAYU SELATAN, JAKARTA TIMUR 13120",
        "landmark": null,
        "phone_code": "+966",
        "postal_code": "JK0701",
        "country_code": "SA",
        "district": "XYZ",
        "lat": 10.01,
        "long": 10.2
    },
    "drop_info": {
        "city": "JK0703",
        "name": "amal .",
        "email": "a_maal11@hotmail.com",
        "phone": "558022554",
        "state": "Al-Riyadh",
        "address": "JALAN PANJANG NO. 08, JAKARTA BARAT",
        "landmark": null,
        "phone_code": "+966",
        "postal_code": "JK0703",
        "country_code": "AE",
        "district": "XYZ",
        "lat": 10.01,
        "long": 10.2
    },
    "return_info": {
        "city": "Riyadh",
        "name": "www.stylishop.com",
        "email": "hello.ksa@stylishop.com",
        "phone": "8001111090",
        "state": "Al-Riyadh",
        "address": "Retail Cart Trading Co., Makhzan2 New Warehouse, Al Bariah",
        "landmark": null,
        "phone_code": "+966",
        "postal_code": "New Industrial Area",
        "country_code": "SA",
        "district": "XYZ",
        "lat": 10.01,
        "long": 10.2
    },
    "shipment_details": {
        "items": [{
            "sku": "3007940106",
            "price": 35.00,
            "quantity": 1,
            "description": "Sample"
        }, {
            "sku": "3007930106",
            "price": 35.00,
            "quantity": 1,
            "description": "Sample"
        }],
        "height": 10,
        "length": 10,
        "weight": 10,
        "breadth": 10,
        "cod_value": 0,
        "order_type": "PREPAID",
        "invoice_date": "2020-01-30",
        "currency_code": "SAR",
        "delivery_type": "FORWARD",
        "invoice_value": 375,
        "invoice_number": "3000020284",
        "reference_number": "test3000019526",
        "courier_partner": 2
    },
    "tax_info": null,
    "additional": {
        "rvp_reason": "Customer wants to return the product",
        "async": false,
        "label": true,
        "order_date": "2020-01-30T20:14:34",
        "vendor_code": "ADDR12182_1463",
        "account_code": "SMSA Domestic",
        "order_id": "Order Number of the Shipment",
        "invoice_base_64": "base_64_string_of_invoice",
        "duty_fee_paid_by":"S"
    }
}
```

> __Response__

```json
{
    "meta": {
        "success": true,
        "message": "Order Placed Successfully",
        "status": 200
    },
    "result": {
        "label": null,
        "reference_number": "test13000019524",
        "security_key": "b43c6e93-e555-44c5-ab76-f57090f78a40",
        "waybill": "test13000019524",
        "sort_code": null
    }
}
```

The create order v4 API allows uploading the package details (manifest information) into the courier partner’s system and returns a waybill and label generated by them. You can create single order; errors/warnings will be highlighted in the response.

Details for multiple shipments needs to passed in items array during object creation.

Please note, in case of any validation failure - order will not get created. Please wait for 8 seconds before you reject a rest-request for latency.

The API is a HTTP POST request to: `https://www.clickpost.in/api/v4/create-order/` where output format is json.

Listed below are the parameters:

####URL parameters:
Parameter | Type | Description
--------- | ---- | -----------
Username | character | User name provided to you by Clickpost team
key | character | API key provided to you by Clickpost team

###Fields Explanation [Payload]

####pickup_info: [pickup location information]
Parameter | Type | Description
--------- | ---- | ----------- 
name | character (100 characters) | name of person at pickup location which shall be contacted by courier partner
email | character (100 characters) | email of the person at pickup location
phone_code | character | ISO phone code of the country where the pickup is to be done. Country and their phone codes: https://www.clickpost.in/api/v1/countries/
phone | character (11 characters) | phone number of the person at pickup location
address | character (500 character) | address of pickup location
postal_code | character (50 character) | postal code of the pickup location. For MENA region, this field represents area code
city | character (200 character) | city of the pickup location
district | character (200 character) | district of the pickup location [Required for South East Asian countries]
state | character (200 character) | state of the pickup location
country_code | character | ISO country code of the country where pickup is to be done. Country code list: https://www.clickpost.in/api/v1/countries/
lat | float | latitute of the pickup location
long | float | longitud of the pickup location

####drop_info (mandatory): [destination location information]
Parameter | Type | Description
--------- | ---- | ----------- 
name | character (100 characters) | name of person at destination location who will be contacted by courier partner
email | character (100 characters) | email of the person at destination location
phone_code | character | ISO phone code of the country where the delivery is to be done. Country and their phone codes: https://www.clickpost.in/api/v1/countries/
phone | character (11 characters) | phone number of the person at destination location
address | character (500 character) | address of destination location
postal_code | character (50 character) | postal code of the destination location. For MENA region, this field represents area code
city | character (200 character) | city of the destination location
district | character (200 character) | district of the destination location [Required for South East Asian countries]
state | character (200 character) | state of the destination location
country_code | character | ISO country code of the country where destination is to be done. Country code list: https://www.clickpost.in/api/v1/countries/
lat | float | latitute of the destination location
long | float | longitud of the destination location

####shipment_info: [shipment information]
Parameter | Type | Description
--------- | ---- | ----------- 
order_type | string | type of shipment based on payment mode [Possible values: "COD", "PREPAID"] 
invoice_value | float | declared value of the shipment
cod_amount | float | cash on delivery amount, that courier has to collect while delivering the shipment
currency_code | string (3 characters) | ISO currency code of currency selected by customer for placing the order: Currency codes in Clickpost https://www.clickpost.in/api/v1/countries/ [https://en.wikipedia.org/wiki/ISO_4217]
reference_number | string (50 characters) | unique shipment ID for the shipment. (You can perform search on this parameter on Clickpost dashboard)
length | int | length in cms
height | int | height in cms
breadth | int | breadth in cms
weight | int | weight in grams

Clickpost also accepts item (SKU: Stock Keeping Unit) level information with the shipment information, which enables you to use Clickpost's returns platform. Please pass following attributes of item [SKU]:

Parameter | Type | Description
--------- | ---- | ----------- 
sku | string (50 character) | SKU (Stock Keeping Unit) ID of the item
description | string (500 characters) | SKU description
quantity | int | quantity of SKU ordered by customer
price | float | price of 1 unit
images | string (1000 character) | image URL of the SKU
return_days | int | eligible days for return from the date, shipment was delivered to customer

####additional (optional): extra information about shipment used to power tracking page:
Parameter | Type | Description
--------- | ---- | ----------- 
order_date | character | timestamp when the order was placed in yyyy-mm-dd format
ship_date | character | timestamp when order was ready to ship in yyyy-mm-dd format
min_edd | integer | minimum days commited to the customer for 1st delivery attempt
max_edd | integer | maximum days commited to the customer for 1st delivery attempt
enable_whatsapp | boolean | if you have whatsapp for business account, you can pass opt-in information here so Clickpost starts sending out communications to customers
order_id | character [50 characters] | order ID of the shipment
invoice_base_64 | character | base 64 string of invoice. Required by DHL for PLT (Paper Less Trade) process
rvp_reason | character | mandatory for reverse pickups [pickups from customer location]. Not required for forward, warehouse to customer 
duty_fee_paid_by | character | defines who will be paying the duty charges for the shipment. Possible values: "S": Shipper, "R": Recipient [only applicable for UPS / DHL]

<aside class="warning">
You must replace Username/key with the username/key provided to you.
</aside>

##Fetch AWB Number / Reference number for already manifested order
> URL (To fetch awb / courier_partner for a reference_number):

```
https://www.clickpost.in/api/v3/create-order?key=<api-key>&reference_number=<reference_number>
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```

> __Response__

```json
{
    "meta": {
        "message": "Success",
        "status": 200,
        "success": true
    },
    "result": {
        "security_key": "560fee51-1af3-4d1d-a6e8-0149b0868d38",
        "courier_partner": 1,
        "reference_number": "100035710-1-2-3",
        "label": "https://pyck-res-bucket.s3.amazonaws.com:443/FEDEX/2019-03-31/8505644567.pdf",
        "waybill": "8505644567"
    }
}
```

> URL (To check reference_number for an awb):

```
https://www.clickpost.in/api/v3/create-order?key=<api-key>&cp_id=<courier_partner_id>&awb=<waybill>
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```

> __Response__

```json
{
    "meta": {
        "message": "Success",
        "status": 200,
        "success": true
    },
    "result": {
        "security_key": "560fee51-1af3-4d1d-a6e8-0149b0868d45",
        "courier_partner": 1,
        "reference_number": "100035710-1-2-3",
        "label": "https://pyck-res-bucket.s3.amazonaws.com:443/FEDEX/2019-03-31/8505644567.pdf",
        "waybill": "8505644567",
        "sort_code": null
    }
}
```

The API is a HTTP GET request to: `https://www.clickpost.in/api/v3/create-order/` where output format is json.

The create-order GET API helps customers to fetch awb and shipping label for already manifested order before requesting for the AWB again for same shipment.

key is compulsory to pass for authentication. You must pass either reference_number or (cp_id and awb) in the API to get the result.

Listed below are the parameters:
####URL parameters:
Parameter | Type | Description
--------- | ---- | -----------
key | character | API key provided to you (mandatory)
reference_number | character | reference_number passed in the POST payload during manifestation (optional)
cp_id | integer | courier partner ID of Clickpost (optional) [list at <a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>]
awb | character | waybill number of the shipment (optional)


##Fetch shipping label

> URL:

```
https://www.clickpost.in/api/v1/fetch/shippinglabel/?&key=<api-key>&waybill=<waybill>&cp_id=<cp_id>&regenerate=false
Headers: {'Content-type': 'application/json'}

(Username/key needs to be replaced with the username/key provided to you)
```

> __Response__

```json
{
    "result": {
        "shipping_label": "https://pyck-res-bucket.s3.amazonaws.com:443/DELHIVERY/2019-03-01/258731.pdf"
    },
    "meta": {
        "message": "SUCCESS",
        "status": 200,
        "success": true
    }
}
```

Use this API to fetch shipping label for already manifested order. Its a GET API.

Listed below are the parameters:
####URL parameters:
Parameter | Type | Description
--------- | ---- | -----------
key | character | API key provided to you (mandatory)
cp_id | integer | courier partner ID of Clickpost (optional) [list at <a href="http://track.clickpost.in/courier_partner" target="_blank">http://track.clickpost.in/courier_partner</a>]
waybill | character | waybill number of the shipment (optional)


##Processing Async API requests

In case you have account with courier partner which does not support sync API, please follow the steps present here to process the request:

When you hit the request for the 1st time, Clickpost will queue the request and share the response with "meta" --> "status" = 202

> __Response__ [Async order creation request accepted]

```json
{
    "meta": {
        "success": true,
        "message": "Order Placed Successfully",
        "status": 202
    },
    "order_id": 8488542,
    "result": {
        "reference_number": "TEST-ALPHA-132135",
        "waybill": null,
        "label": null,
        "sort_code": null
    }
}
```

Generally it takes 30 sec for the courier to process the request in async manner. Since Clickpost APIs are idempotent, you can continue to make the order creation request with same parameters, Clickpost will check the reference number and will return "meta" --> "status" 102 if the request is still under process:

> __Response__ [Async order creation request in process]

```json
{
    "order_id": 8488863,
    "result": {
        "waybill": null,
        "sort_code": null,
        "security_key": null,
        "label": null,
        "reference_number": "TEST-ALPHA-132135"
    },
    "meta": {
        "message": "We are processing your order",
        "success": false,
        "status": 102
    }
}
```

Once the request is processed and you make the polling call with same reference number on the same API, you will get success [status code 200 or 323] or failure depending on response from courier partner

> __Response__ [Async order creation Success]

```json
{
    "meta": {
        "status": 323,
        "message": "You have already placed this order",
        "success": false
    },
    "result": {
        "waybill": "1993933981231",
        "sort_code": null,
        "reference_number": "AR9-19-2697",
        "label": "https://test-bucket.s3.amazonaws.com:443/test/2019-09-23/19939339821.pdf",
        "security_key": "f60207d9-8bd9-441c-80e9-0c3781721fed"
    },
    "tracking_id": 52158761,
    "order_id": 7127897
}

```

> __Response__ [Async order creation failure]

```json
{
    "order_id": 8488743,
    "meta": {
        "message": "{'status': {'reason': 'ConfigurationError<FAAS: warehouses<GURGOANTHEA> has not been configured>', 'job_id': 'b3f5be04-f916-4bef-b0d4-3d8753e8332f', 'success': False, 'value': 'ConfigurationError', 'type': 'Complete'}}",
        "success": false,
        "status": 319
    },
    "reference_number": "TEST-ALPHA-132135"
}
```





----------
