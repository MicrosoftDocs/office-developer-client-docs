---
title: "SizedSRowSet"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedSRowSet
api_type:
- COM
ms.assetid: 419e2c6d-ac3b-46c6-9a12-33f51f6d7f12
description: "Last modified: March 09, 2015"
---

# SizedSRowSet

**Applies to**: Outlook 
  
Creates a named [SRowSet](srowset.md) structure that contains a specified number of rows. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**SRowSet** <br/> |
   
```cpp
SizedSRowSet (_crow, _name)
```

## Parameters

__crow_
  
> Count of the number of rows to be included in the new structure.
    
__name_
  
> Name for the new structure.
    
## Remarks

To use the new structure that results from the **SizedSRowSet** macro as a pointer to an **SRowSet** structure, perform the following cast: 
  
```cpp
lpSRowSet = (LPSRowSet) &SizedSRowSet;

```

## See also

- [SRowSet](srowset.md)
- [Macros Related to Structures](macros-related-to-structures.md)

