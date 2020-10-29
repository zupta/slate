---
title: API Reference

language_tabs:
  - json

toc_footers:
  - <!--a href='#'>Sign Up for a Developer Key</a-->
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:

  - recommend
  - create
  - track
  - cancellation
  - serviceability
  - expected_date_of_delivery
  - pickup
  - customer_feedback
  - ndr_action_update
  - whatsapp_optin
  - status
  - error

search: true
---

# Introduction

Welcome to the Clickpost API! You can use our API to access Clickpost API endpoints which can get information on our different APIs:

1. __Recommendation Engine API__: Recommend list of Courier Partners in priority order
2. __Manifestation API__: Create order on Courier Partner and fetch AWB, Cancel orders and place pickup request
3. __Shipping Label Generation API__: Generating new shipping label or get the one generated in Manifestation Request
4. __Track Shipment API__: Track your shipment using AWB and Courier Partner.
5. __Cancellation API__: Cancel shipment manifested on Courier Partner for faster returns and higher inventory availability
6. __Serviceability, Cost, TAT API__: Check pincode serviceability, cost for shipping and turn around time for the delivery.
7. __Expected Date of Delivery API__: Check predictive sla time range for any shipment
8. __Pickup Request API__: Recommend list of Courier Partners in priority order
9. __Operation and Customer Feedback API__: Gives list of customer feedbacks and operations feedback on the tracking page.
10. __NDR Action update API__: Updates the after NDR action directly on courier company's database.
11. __Return Webhooks__: Track your return shipment using AWB and Courier Partner using webhooks (we give data on your endpoint).
12. __Whatsapp Optin-Optout__: In case customer sends whatsapp optout communication to you, you can update the same in Clickpost using this API 

<!--We have language bindings in Shell, Ruby, PHP and Python!-->

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.
