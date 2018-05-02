---
title: "CbNewFLATMTSIDLIST"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.CbNewFLATMTSIDLIST
api_type:
- COM
ms.assetid: 26628646-7948-4341-aaef-5c476a857a52
description: "Last modified: March 09, 2015"
---

# CbNewFLATMTSIDLIST

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Computes the number of bytes that should be allocated for a new [FLATMTSIDLIST](flatmtsidlist.md) structure that contains several [MTSID](mtsid.md) structures of a specified size. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**FLATMTSIDLIST** <br/> |
   
```
CbNewFLATMTSIDIDLIST (_cb)
```

## Parameters

 __cb_
  
> Count of bytes in the **MTSID** structures to be included in the new **FLATMTSIDLIST** structure. 
    
## See also

#### Reference

[FLATMTSIDLIST](flatmtsidlist.md)
  
[MTSID](mtsid.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

