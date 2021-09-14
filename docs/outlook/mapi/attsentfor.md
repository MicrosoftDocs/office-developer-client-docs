---
title: "attSentFor"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: aa8c8d64-d2a0-4cdf-a8aa-21c8d0a0a3fc
description: "Last modified: July 23, 2011"
 
 
---

# attSentFor

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The **attSentFor** attribute is encoded as counted strings laid end-to-end. The format for **attSentFor** is as follows: 
  
 **attSentFor**: 
  
> display-name-length display-name address-length  _email-address_
    
 _email-address_
  
> type **:** address 
    
Unlike other length values, the display-name-length and address-length are unsigned 16-bit values instead of unsigned long integers. They still include terminating null characters, however. The type and address strings in the  _email-address_ entry are separated by a literal colon (:) character, such as "smtp:joe@nowhere.com". Only the combined type **:**address string is null-terminated.
  

