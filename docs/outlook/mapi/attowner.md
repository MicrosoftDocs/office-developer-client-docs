---
title: "attOwner"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 3c6a4050-fd97-42ce-abb1-118254b367bd
description: "Last modified: July 23, 2011"
---

# attOwner

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
The **attOwner** attribute is encoded as counted strings laid end-to-end. The format for **attOwner** is as follows: 
  
 **attOwner**: 
  
> display-name-length display-name address-length  _email-address_
    
 _email-address_
  
> type **:** address 
    
Unlike other length values, the display-name-length and address-length are unsigned 16-bit values instead of unsigned long integers. They still include terminating null characters, however. The type and address strings in the  _email-address_ entry are separated by a literal colon (:) character, such as "smtp:joe@nowhere.com". Only the combined type **:**address string is null-terminated.
  
The mapping of MAPI properties to the **attOwner** attribute is dependent on the message class of the message being encoded. 
  

