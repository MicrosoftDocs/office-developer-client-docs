---
title: "FBadRowSet"
description: Describes FBadRowSet and provides syntax, parameters, and return value.
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FBadRowSet
api_type:
- COM
ms.assetid: 3890dd50-e6ca-4859-bada-f6752ab61d41
---

# FBadRowSet

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Validates all table rows included in a set of table rows.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```cpp
BOOL FBadRowSet(
  LPSRowSet lpRowSet
);
```

## Parameters

 _lpRowSet_
  
> [in] Pointer to an [SRowSet](srowset.md) structure identifying the row set to be validated. If the pointer is NULL, the structure is invalid. 
    
## Return value

TRUE 
  
> A row of the specified row set is invalid, or the row set itself is invalid. 
    
FALSE 
  
> The rows of the specified row set and the row set itself are all valid.
    
## See also



[FBadRow](fbadrow.md)

