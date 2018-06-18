---
title: "CbNewSSortOrderSet"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.CbNewSSortOrderSet
api_type:
- COM
ms.assetid: a2fb67e0-ccdb-4eb0-9f8c-75213442159f
description: "Last modified: March 09, 2015"
---

# CbNewSSortOrderSet

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Computes the number of bytes to be allocated for a new [SizedSSortOrderSet](sizedssortorderset.md) structure that contains a specified number of sort orders represented by [SSortOrder](ssortorder.md) structures. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**SSortOrderSet** <br/> |
   
```cpp
CbNewSSortOrderSet (_csort)
```

## Parameters

 __csort_
  
> Count of **SSortOrder** structures to be included in the **SSortOrderSet** structure. 
    
## See also



[SizedSSortOrderSet](sizedssortorderset.md)
  
[SSortOrder](ssortorder.md)


[Macros Related to Structures](macros-related-to-structures.md)

