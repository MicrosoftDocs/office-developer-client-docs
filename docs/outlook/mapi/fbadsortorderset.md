---
title: "FBadSortOrderSet"
description: Describes FBadSortOrderSet and provides syntax, parameters, and return value.
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FBadSortOrderSet
api_type:
- COM
ms.assetid: b7f80e0a-8ddd-4b24-ab63-2078a8152058
---

# FBadSortOrderSet

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Validates a sort order set by verifying its memory allocation. 
  
|Key|Value |
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```cpp
ULONG FBadSortOrderSet(
  LPSSortOrderSet lpsos
);
```

## Parameters

 _lpsos_
  
> [in] Pointer to an [SSortOrderSet](ssortorderset.md) structure identifying the sort order set to be validated. 
    
## Return value

TRUE 
  
> The specified sort order set is invalid. 
    
FALSE 
  
> The specified sort order set is valid.
    
## Remarks

The **FBadSortOrderSet** function can be used to prepare for a call to a sort method such as the [IMAPITable::SortTable](imapitable-sorttable.md) method. 
  

