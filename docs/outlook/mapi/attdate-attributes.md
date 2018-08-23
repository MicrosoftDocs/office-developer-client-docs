---
title: "attDate Attributes"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 22801641-752c-4c81-be90-02039eaa4277
description: "Last modified: July 23, 2011"
 
 
---

# attDate Attributes

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
All MAPI properties relating to dates and times are mapped to TNEF attributes that have the **attDate** prefix. These are all encoded as **DTR** structures. The dates and times for attachment attributes are encoded as **DTR** structures as well. 
  
All MAPI properties relating to dates and times are mapped to TNEF attributes that have the **attDate** prefix. These are all encoded as **DTR** structures. The dates and times for attachment attributes are encoded as **DTR** structures as well. 
  
A **DTR** structure is very similar to the **SYSTEMTIME** structure defined in the Win32 header files. The **DTR** structure is encoded in the TNEF stream as **sizeof(DTR)** bytes starting with the first member of the structure. The **DTR** structure is defined in the TNEF.H header file. 
  

