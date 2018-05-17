---
title: "MSCAP_SELECTOR"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f28ac144-f5ac-fd83-2b72-8d6e5fd74b6e
description: "Last modified: July 23, 2011"
---

# MSCAP_SELECTOR

  
  
**Applies to**: Outlook 
  
Specifies the capabilities to return for a store.
  
## Quick Info

```
typedef enum 
{ 
    MSCAP_SEL_RESERVED1 = 0, 
    MSCAP_SEL_RESERVED2, 
    MSCAP_SEL_FOLDER, 
    MSCAP_SEL_RESERVED3, 
    MSCAP_SEL_RESTRICTION, 
} MSCAP_SELECTOR;
```

## Members

 *MSCAP_SEL_RESERVED1* 
  
> This member is reserved for the internal use of Outlook and is not supported. 
    
 *MSCAP_SEL_RESERVED2* 
  
> This member is reserved for the internal use of Outlook and is not supported. 
    
 *MSCAP_SEL_FOLDER* 
  
> Capabilities about supporting folders on a store.
    
 *MSCAP_SEL_RESERVED3* 
  
> This member is reserved for the internal use of Outlook and is not supported. 
    
 *MSCAP_SEL_RESTRICTION* 
  
> Capabilities about supporting restrictions on a store.
    

