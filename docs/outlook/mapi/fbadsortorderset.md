---
title: "FBadSortOrderSet"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FBadSortOrderSet
api_type:
- COM
ms.assetid: b7f80e0a-8ddd-4b24-ab63-2078a8152058
description: "Last modified: March 09, 2015"
---

# FBadSortOrderSet

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Validates a sort order set by verifying its memory allocation. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```
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
  

