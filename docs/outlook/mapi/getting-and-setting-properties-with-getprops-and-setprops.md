---
title: "Getting and setting properties with GetProps and SetProps"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 309d2b3d-dc71-4222-b293-4bfc467b5429
description: "Last modified: July 23, 2011"
---

# Getting and setting properties with GetProps and SetProps
 
**Applies to**: Outlook 2013 | Outlook 2016 
  
Whenever possible, try to retrieve or modify a property with the [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPIProp::SetProps](imapiprop-setprops.md) methods. Unless the property you are working with is very large, these methods should be adequate. The other alternative is to read from or write to a stream with the [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) interface. Streams can handle very large properties successfully, but they are a greater drain on resources because they require the COM libraries. Use the **IStream** interface only after your call to **IMAPIProp::GetProps** or **IMAPIProp::SetProps** fails. 
  

