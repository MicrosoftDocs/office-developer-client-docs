---
title: "CbNewADRLIST"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.CbNewADRLIST
api_type:
- COM
ms.assetid: 9ec1bbaa-7707-4239-9994-21ad1116430b
description: "Last modified: March 09, 2015"
---

# CbNewADRLIST

  
  
**Applies to**: Outlook 
  
Computes the number of bytes that should be allocated for a new [ADRLIST](adrlist.md) structure that contains a specified number of recipients represented by [ADRENTRY](adrentry.md) structures. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**ADRLIST** <br/> |
   
```cpp
CbNewADRLIST (_centries)
```

## Parameters

 __centries_
  
> Count of **ADRENTRY** structures to be included in the new **ADRLIST** structure. 
    
## See also



[ADRLIST](adrlist.md)
  
[ADRENTRY](adrentry.md)


[Macros Related to Structures](macros-related-to-structures.md)

