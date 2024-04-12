---
title: "FBadRestriction"
description: "FBadRestriction validates a restriction used to limit a table view. This article describes its syntax, parameters, return value, and remarks."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- FBadRestriction
api_type:
- HeaderDef
ms.assetid: 6ad3638c-d088-4a89-9b0d-f5b672162203
---

# FBadRestriction

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Validates a restriction used to limit a table view. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```cpp
ULONG FBadRestriction(
  LPSRestriction lpres
);
```

## Parameters

 _lpres_
  
> [in] An [SRestriction](srestriction.md) structure defining the restriction to be validated. 
    
## Return value

TRUE 
  
> The specified restriction, or one or more of its subrestrictions, is invalid. 
    
FALSE 
  
> The specified restriction and all its subrestrictions are valid.
    
## Remarks

Once a restriction is validated, it can be passed in calls to the [IMAPITable::Restrict](imapitable-restrict.md) method to restrict the table to certain rows, to the [IMAPITable::FindRow](imapitable-findrow.md) method to locate a table row, and to methods of the [IMAPIContainer](imapicontainerimapiprop.md) interface to perform a restriction on a container object. 
  

