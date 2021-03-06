# Tracking Status Codes

clickpost_status_code | clickpost_status_description | Meaning
----- | ------ |  -------
1 | ORDER_PLACED | 'Order Has Been Placed / Manifested on Courier Partner'
2 | PICKUP_PENDING | 'Pickup Pending'
3 | PICKUP_FAILED | 'Pickup Failed'
4 | PICKED_UP | 'Pickup Has Been Done'
5 | INTRANSIT | 'In Transit'
6 | OUT_FOR_DELIVERY | 'Shipment Out For Delivery'
7 | NOT_SERVICEABLE | 'Area For Delivery Is Not Servicable'
8 | DELIVERED | 'Shipment Delivered'
9 | FAILED_DELIVERY | 'Delivery Failed'
10 | CANCELLED_ORDER | 'Order Has Been Cancelled'
11 | RTO_REQUESTED | 'Rto For Shipment has been Requested'
12 | RTO     | 'Marked As Return'
13 | RTO_OUT_FOR_DELIVERY | 'Shipment Is Out For Delivery For RTO'
14 | RTO_DELIVERED | 'RTO Delivered'
15 | RTO_FAILED | 'RTO Failed'
16 | LOST     | 'Shipment is Lost'
17 | DAMAGED     | 'Shipment is damaged'
18 | SHIPMENT_DELAYED | 'Shipment Is Delayed Or Misroute'
19 | CONTACT_CUSTOMER_CARE | 'Contact To The Customer Care'
20 | SHIPMENT_HELD | 'Shipment Is being held'
21 | RTO_INTRANSIT | 'RTO In Transit'
25 | OUT_FOR_PICKUP | 'Shipment Out For Pickup' (Important in Marketplace / RVP pickups)
26 | RTO_CONTACT_CUSTOMER_CARE | 'RTO Contact Customer Care'
27 | RTO_SHIPMENT_DELAY | 'RTO Shipment Delayed'
28 | AWB REGISTERED | 'AWB registered on Clickpost'
30 | EXCHANGE_PICKUP | 'Exchange successful, Shipment delivered and picked up from the customer' [Only for exchange service]
31 | EXCHANGE_INTRANSIT | 'Exchanged shipment In Transit to warehouse' [Only for exchange service]
32 | EXCHANGE_DELIVERED | 'When an exchange shipment is delivered back' [Only for exchange service]
101| RETURN ORDER PLACED | 'Order Placed in Clickpost for reverse pickup by Customer' # Only useful for customers using Returns Management Platform of Clickpost

Status flow diagram is available at: http://bit.ly/status_flow

It is strongly recommended to use the clickpost_status_code to apply any logic on unified statuses.