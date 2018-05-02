---
title: "SizedSPropProblemArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedSPropProblemArray
api_type:
- COM
ms.assetid: 2fc3febb-8c69-4315-a112-a28eee98013d
description: "Last modified: March 09, 2015"
---

# SizedSPropProblemArray

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Creates a named [SPropProblemArray](spropproblemarray.md) structure that contains a specified number of [SPropProblem](spropproblem.md) structures. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**SPropProblemArray** <br/> |
   
```
SizedSPropProblemArray(_cprob, _name)
```

## Parameters

 __ cprob_
  
> Count of **SPropProblem** structures to be included in the new structure. 
    
 __ name_
  
> Name for the new structure.
    
## Remarks

Use the **SizedSPropProblemArray** macro to create a property problem array with explicit bounds. To use the new structure that results from the **SizedSPropProblemArray** macro as a pointer to an **SPropProblemArray** structure, perform the following cast: 
  
```
lpPropProbArray = (LPSPropProblemArray) &amp;SizedSPropProblemArray;
```

## See also

#### Reference

[SPropProblemArray](spropproblemarray.md)
  
[SPropProblem](spropproblem.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

