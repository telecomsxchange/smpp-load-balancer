# smpp-load-balancer

** Goal ** 

Scale the message per second performance of SMPP proxy project. 

A single threaded (For Now) proxy load balancer version that would only do connection binding authentication from clients and then relay all SMS messages to the upstream group of proxies that would do the authorization/routing and communication with vendors. 

This way we would be able to distribute the load between multiple single threaded proxy instances similar to what we'd do for SIP with kamailio and B2BUA. 

*Next Steps*

- We develop smpp proxy load balancer. 
- Store existing global smpp data to DB, so that all instances share same rate/limit configuration values.
- Extend SMPP protocol for authentication and connection "marking and saving" to ensure correct DR and SMPP responses routing. 
- Resolve inbound DID scenario, like Nexmo. 

*Risks & known issues*

The issue and risk with this approach is that you may face a bottle neck in proxy load balancer, because it would still be single threaded  

It will not be very easy to replace it with something else later, because the balancer would require us to extend a bit SMPP standard protocols to relay authentication info and smpp connection info.
