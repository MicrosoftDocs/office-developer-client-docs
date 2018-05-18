---
title: "FBadColumnSet"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- FBadColumnSet
api_type:
- HeaderDef
ms.assetid: 15be5a8c-4299-4434-b521-c901215b9dda
description: "Last modified: March 09, 2015"
---

# FBadColumnSet

  
  
**Applies to**: Outlook 
  
Tests the validity of a table column set for use by a service provider in a subsequent call to the [IMAPITable::SetColumns](imapitable-setcolumns.md) method. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```cpp
ULONG FBadColumnSet(
  LPSPropTagArray lpptaCols
);
```

## Parameters

 _lpptaCols_
  
> [in] Pointer to an [SPropTagArray](sproptagarray.md) structure that contains an array of property tags defining the table columns to validate. 
    
## Return value

TRUE 
  
> The specified column set is invalid. 
    
FALSE 
  
> The specified column set is valid.
    
## Remarks

The **FBadColumnSet** function treats columns of type PT_ERROR as invalid and columns of type PT_NULL as valid. 
  

