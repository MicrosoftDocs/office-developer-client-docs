---
title: "SizedSPropTagArray"
description: Outlines SizedSPropTagArray, which creates a named SPropTagArray structure that includes a specified number of property tags. 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SizedSPropTagArray
api_type:
- COM
ms.assetid: 1d2dc6e9-735d-4b5b-af6f-adf6a32a666d
---

# SizedSPropTagArray

**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a named [SPropTagArray](sproptagarray.md) structure that includes a specified number of property tags. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**SPropTagArray** <br/> |
   
```cpp
SizedSPropTagArray (_ctag, _name)
```

## Parameters

__ctag_
  
> Count of property tags to be included in the new structure.
    
__name_
  
> Name for the new structure.
    
## Remarks

Use the **SizedSPropTagArray** macro to create a property tag array with explicit bounds. 
  
To use the new structure that results from the **SizedSPropTagArray** macro as a pointer to an **SPropTagArray** structure, perform the following cast: 
  
```cpp
lpPropTagArray = (LPPropTagArray) &SizedSPropTagArray;

```

## See also

- [SPropTagArray](sproptagarray.md)
- [Macros Related to Structures](macros-related-to-structures.md)

