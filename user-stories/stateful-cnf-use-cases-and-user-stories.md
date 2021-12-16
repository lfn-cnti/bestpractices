# Stateful CNF - Use Cases & User Stories

## Stateful / Persistent data

### Use Case
As a CSP, I must maintain persistent data (such as subscriber information, account balances, quota balances, thresholds, etc.) for the subscribers that use my network and/or services.   This persistent data can be static or dynamic in nature.  In many cases, the persistent data is maintained for the lifetime of a subscriber’s account.
### User Stories
1. A subscriber wants to update his/her address with a CSP.  To allow for this, a CSP must be able to maintain persistent data (static) such as the subscriber identity, subscribed services, selected features, etc. 
2. A subscriber wants to use the services offered by a CSP.  To provide service to a subscriber, a CSP must maintain persistent data (dynamic) regarding the subscriber such as an account balance, quota balance, thresholds, etc. This data is then utilized to trigger a host of business decisions such as QoS changes, moving a call/session from one access network to another, allowing or denying access to a service, etc.

## Real-time / Low Latency CRUD actions

### Use Case
As a CSP, I must be able to perform real-time CRUD actions on persistent data (dynamic) to limit financial exposure and to support diverse business, network, and service decisions such as changing a subscriber’s QoS, changing the service access method, granting access to a service, limiting, or denying access to a service, etc. 

### User Stories
1. A subscriber attempts to access a CSP service (e.g., a data service).  A real-time request is made to determine if the subscriber has sufficient quota (stored as persistent data) available to allow access to the service.  If quota is available, access to the service is granted in real-time.  If not, access may be denied, limited, or an alternative proposed. 
2.	As the subscriber is using the CSP service, quota is updated (stored as persistent data) in real-time to accurately reflect consumption at any given time.  In addition, the quota is maintained in real-time to serve as a basis for decision making (business, service, or financial by the CSP)
3.	An IoT device in a smart factory attempts to access a higher QoS network slice service to accommodate a spike in production.  A real-time request is made to determine if the IoT device has utilized its High Bandwidth QoS threshold for the day or not.  If the threshold has not yet been reached, access to the higher QoS is granted.  Otherwise, the IoT device is denied access. 

## High Transaction Processing Throughput

### Use Case
As a CSP, I must be able to achieve high throughput for CRUD actions on persistent data.  In some scenarios, this could amount to hundreds of thousands of transactions per second. 

### User Stories
1. A subscriber of a large CSP wants to access and use services on the CSP’s network.  At any given point in time, millions of subscribers and devices may be attempting to access and use services at the same time.  Therefore, persistent data must be created, read, updated, and deleted in real-time to support a wide variety of business, network, and service decisions.  The sheer number of subscribers and devices demands that hundreds of thousands of such CRUD actions per second be possible.  Without this capability, the CSP is unable to determine if a subscriber should be allowed to use the service without being exposed to financial risk or being unable to make various business, network and services decisions based on real-time data.     

## ACID Compliant

### Use Case
As a CSP, I must ensure that all financially related transactions impacting (or using) persistent data are ACID compliant (Atomicity, Consistency, Isolation, Durability). 

### User Stories
1. As a subscriber to services provided by a CSP, certain events, transactions, and activities can create financial obligations to the CSP and vice versa.  As such, these transactions must be kept as persistent data and must be ACID compliant to guarantee their accuracy at any given time. 

## Availability

### Use Case
As a CSP, I must continuously provide persistent data to stateless services that need (and have permission) to access the information.  

### User Stories
1. A subscriber of telecommunication services expects services to be available 24/7/365, therefore CSPs must be able to provide high availability of persistent data which is used for business, network, and service decisions.

## Continuity

### Use Case
As a CSP, I must be able to ensure “instant and total” recovery of persistent data in the event of a local or even complete site failure. 
### User Stories
1. A subscriber of telecommunication services expects services to be available 24/7/365, therefore CSPs must be able to provide continuity of persistent data in the event of a catastrophic failure.   Without continuity, decisions on behalf of the subscriber would not be possible or be based on inaccurate information.   The expectation of continuity is expressed as the ability to recover all persistent data instantly and totally. 
