# Error Codes

The Clickpost API uses the following error codes:

Server Response Code | Meaning
---------- | -------
200 | Success
400 | Bad Request
401 | Unauthorized
403 | Forbidden
404 | Not Found
405 | Method Not Allowed
406 | Not Acceptable
429 | Too Many Requests
500 | Internal Server Error
503 | Service Unavailable
504 | Server unable to serve the request, please retry

Clickpost Service Error Code | Meaning
---------- | -------
301 | Authentication Failed: Invalid Token or API Key
302 | Invalid Courier Partner Id with Field cp_id
303 | waybill already registered
304 | Already Registered For Service
306 | You are not Registered To Use this service, Please Register
316 | You Dont Have Credentials For The Courier Partner
320 | This service is not subscribed by you
324 | You Are Using Invalid Credential For Courier Partner, Please Update
325 | Status You Are Trying to update is invalid for our systems, Contact to tech@clickpost.in
326 | Invalid Tracking Id
328 | Invalid POST data
330 | waybill does not exist
351 | No account exist
352 | Multiple Account exist
353 | Inactive account
354 | Unhandled CP error
355 | Vendor code not found
422 | Invalid Entity

Order Creation Error Code | Meaning
---------- | -------
307 | You have entered invalid Order Type
308 | You have entered invalid Order priority
309 | Invalid Delivery Type
310 | RVP reason is missing
311 | Invalid Courier Partner For RVP
312 | Items Data is missing from order details
313 | Invalid Format of items for Order data
314 | Invalid Format Of Order Data
315 | Invalid Cod Value
319 | Error In Order Placing To Courier Partner
321 | Awb Number Does not exist in system for courier partner
322 | Internal Server Error In Courier Partners Server, Try Again
323 | You have Already placed this order

Clickpost Webhook Error Code | Meaning
---------- | -------
305 | Webhook already Registered for the user
327 | Webhook not registered for the user

Order Cancellation Error Code | Meaning
---------- | -------
600 | Order already cancelled
350 | Order Cancellation Error