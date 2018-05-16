---
title: "FBadRow"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FBadRow
api_type:
- COM
ms.assetid: 205d00df-488d-4888-8782-a1f70f54d720
description: "Last modified: March 09, 2015"
---

# FBadRow

  
  
**Applies to**: Outlook 
  
Validates a row in a table.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```
ULONG FBadRow(
  LPSRow lprow
);
```

## Parameters

 _lprow_
  
> [in] Pointer to an [SRow](srow.md) structure identifying the row to be validated. 
    
## Return value

TRUE 
  
> The specified row is invalid.
    
FALSE 
  
> The specified row is valid.
    
## See also

#### Reference

[FBadRowSet](fbadrowset.md)

