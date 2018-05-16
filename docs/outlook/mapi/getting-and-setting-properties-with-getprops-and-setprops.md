---
title: "Getting and Setting Properties with GetProps and SetProps"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 309d2b3d-dc71-4222-b293-4bfc467b5429
description: "Last modified: July 23, 2011"
 
 
---

# Getting and Setting Properties with GetProps and SetProps

  
  
**Applies to**: Outlook 
  
Whenever possible, try to retrieve or modify a property with the [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPIProp::SetProps](imapiprop-setprops.md) methods. Unless the property you are working with is very large, these methods should be adequate. The other alternative is to read from or write to a stream with the [IStream](http://msdn.microsoft.com/en-us/library/aa380034%28VS.85%29.aspx) interface. Streams can handle very large properties successfully, but they are a greater drain on resources because they require the COM libraries. Use the **IStream** interface only after your call to **IMAPIProp::GetProps** or **IMAPIProp::SetProps** fails. 
  

