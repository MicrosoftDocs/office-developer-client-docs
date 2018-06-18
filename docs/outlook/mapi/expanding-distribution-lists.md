---
title: "Expanding Distribution Lists"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 44231a95-dafc-44f7-bfa9-9f73ea8cb8b7
description: "Last modified: July 23, 2011"
 
 
---

# Expanding Distribution Lists

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 **To prompt MAPI to expand a distribution list**
  
- Set its **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md)) property to MAPIPDL.
    
    MAPI expands addresses with this type before sending the message to the transport provider.
    

