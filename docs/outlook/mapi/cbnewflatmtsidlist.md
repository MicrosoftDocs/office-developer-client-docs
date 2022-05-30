---
title: "CbNewFLATMTSIDLIST"
description: "CbNewFLATMTSIDLIST computes the number of bytes that should be allocated for a new FLATMTSIDLIST structure that contains several MTSID structures of a specified size."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.CbNewFLATMTSIDLIST
api_type:
- COM
ms.assetid: 26628646-7948-4341-aaef-5c476a857a52
---

# CbNewFLATMTSIDLIST

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Computes the number of bytes that should be allocated for a new [FLATMTSIDLIST](flatmtsidlist.md) structure that contains several [MTSID](mtsid.md) structures of a specified size. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**FLATMTSIDLIST** <br/> |
   
```cpp
CbNewFLATMTSIDIDLIST (_cb)
```

## Parameters

 __cb_
  
> Count of bytes in the **MTSID** structures to be included in the new **FLATMTSIDLIST** structure. 
    
## See also



[FLATMTSIDLIST](flatmtsidlist.md)
  
[MTSID](mtsid.md)


[Macros Related to Structures](macros-related-to-structures.md)

