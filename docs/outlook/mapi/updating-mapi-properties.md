---
title: "Updating MAPI Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: faafde3d-3989-4182-91f1-a0cf0f1b5388
description: "Last modified: July 23, 2011"
 
 
---

# Updating MAPI Properties

  
  
**Applies to**: Outlook 
  
Clients and service providers can update a property value by calling:
  
- An object's [IMAPIProp::SetProps](imapiprop-setprops.md) method to update the value of one or more of an object's properties. 
    
- The [HrSetOneProp](hrsetoneprop.md) function to update only one property at a time. Use **HrSetOneProp** only if the target object is local; this function can cause performance degradation when used with remote objects. 
    
The following procedure illustrates how to use **SetProps** to update the message class, or PR_MESSAGE_CLASS_A ( [PidTagMessageClass](pidtagmessageclass-canonical-property.md)) property, of a message. 
  
 **To update the message class of a message**
  
1. Allocate an [SPropValue](spropvalue.md) structure for the message class and set its members as appropriate. 
    
  ```
  SPropValue spvMsgClass;
  spvMsgClass.ulPropTag = PR_MESSAGE_CLASS_A;
  spvMsgClass.Value.lpszA = "IPM.NewClass";
   
  ```

2. Call the message's **IMAPIProp::SetProps** method to set the new message class. 
    
  ```
  hRes = lpMessage->SetProps(1, (LPSPropValue) &amp;spvMsgClass, NULL);
  ```

## See also

#### Concepts

[MAPI Property Overview](mapi-property-overview.md)

