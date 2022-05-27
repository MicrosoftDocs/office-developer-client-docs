---
title: "CbNewFLATENTRYLIST"
description: "CbNewFLATENTRYLIST computes the number of bytes that should be allocated for a new FLATENTRYLIST structure that contains several FLATENTRY structures of a specified size."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.CbNewFLATENTRYLIST
api_type:
- COM
ms.assetid: f7182631-7f0e-4f4a-995d-22c0bedd7b6a
---

# CbNewFLATENTRYLIST

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Computes the number of bytes that should be allocated for a new [FLATENTRYLIST](flatentrylist.md) structure that contains several [FLATENTRY](flatentry.md) structures of a specified size. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**FLATENTRYLIST** <br/> |
   
```cpp
CbNewFLATENTRY (_cb)
```

## Parameters

 __cb_
  
> Count of bytes in the **FLATENTRY** structures to be included in the new **FLATENTRYLIST** structure. 
    
## See also



[FLATENTRYLIST](flatentrylist.md)
  
[FLATENTRY](flatentry.md)


[Macros Related to Structures](macros-related-to-structures.md)

