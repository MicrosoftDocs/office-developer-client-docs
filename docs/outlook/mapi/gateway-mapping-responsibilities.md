---
title: "Gateway Mapping Responsibilities"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: ac67bb83-e4f3-4c82-995b-c11a2a195e90
description: "Last modified: July 23, 2011"
---

# Gateway Mapping Responsibilities

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
When a MAPI-aware gateway receives a message containing named properties in one of the special property sets designated to contain gateway-mappable properties, the gateway should map all of the properties to the protocol of the destination messaging system. Although MAPI recommends that gateways handle all named properties in the special property sets, gateways are expected to handle only two: e-mail address and address type. Because the e-mail address and address type properties directly affect message transmission, it is critical that gateways support the mapping of these two properties. Because search keys consist of a user's address type and address, they should also be translated if at all possible.
  
Entry identifiers are not expected to be handled frequently. To enable mapping of an entry identifier that originates in one messaging system to an entry identifier that is usable by another messaging system, the gateway must be able to use the format of both systems. Because most gateways are not aware of entry identifier formats, the translation of entry identifiers is rare.
  
Another mappable property that is not expected to be translated frequently is the display name. Gateways should store display names and transmit them, but not necessarily translate them. 
  

