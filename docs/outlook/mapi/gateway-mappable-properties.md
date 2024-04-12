---
title: "Gateway mappable properties"
description: This article provides an overview of gateway mappable properties.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 3a51ee7e-d030-4f04-915b-ff8bd351207d
---

# Gateway mappable properties

**Applies to**: Outlook 2013 | Outlook 2016 
  
Gateway-mappable properties are properties that may require translation when sent from one messaging domain to another. MAPI's gateway-mappable properties enable messages to include information that requires a gateway to ensure the destination messaging system uses it properly. Although gateway developers are not required to provide this translation capability, they should consider gateway-mappable properties as an opportunity to improve handling of message content.
  
MAPI specifies five types of gateway-mappable properties:
  
- Display name
    
- Email address
    
- Email type
    
- Entry identifier
    
- Search key
    
This is the set of addressing properties that are associated with recipients, senders, report recipients, and delegated senders and recipients. To help your client define these properties so that a gateway handles them specially, MAPI specifies a naming convention using named properties and property sets. Five property sets exist to hold named properties, the addressing properties that require mapping. There is one property set for each type of mappable property. The property sets that will hold these named addressing properties are as follows.
  
|**Property set**|**Description**|
|:-----|:-----|
|PS_ROUTING_DISPLAY_NAME  <br/> |Contains string properties used as display names. |
|PS_ROUTING_EMAIL_ADDRESSES  <br/> |Contains string properties used as email addresses. |
|PS_ROUTING_ADDRTYPE  <br/> |Contains string properties used as email address types. |
|PS_ROUTING_ENTRYID  <br/> |Contains binary properties used as long-term entry identifiers. |
|PS_ROUTING_SEARCH_KEY  <br/> |Contains binary properties used as search keys. |
   

