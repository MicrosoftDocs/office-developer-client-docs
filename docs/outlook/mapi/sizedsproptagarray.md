---
title: "SizedSPropTagArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedSPropTagArray
api_type:
- COM
ms.assetid: 1d2dc6e9-735d-4b5b-af6f-adf6a32a666d
description: "Last modified: March 09, 2015"
---

# SizedSPropTagArray

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Creates a named [SPropTagArray](sproptagarray.md) structure that includes a specified number of property tags. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**SPropTagArray** <br/> |
   
```
SizedSPropTagArray (_ctag, _name)
```

## Parameters

_  _ctag_
  
> Count of property tags to be included in the new structure.
    
 __name_
  
> Name for the new structure.
    
## Remarks

Use the **SizedSPropTagArray** macro to create a property tag array with explicit bounds. 
  
To use the new structure that results from the **SizedSPropTagArray** macro as a pointer to an **SPropTagArray** structure, perform the following cast: 
  
```
lpPropTagArray = (LPPropTagArray) &amp;SizedSPropTagArray;

```

## See also

#### Reference

[SPropTagArray](sproptagarray.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

