---
title: "SPropProblemArray"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SPropProblemArray
api_type:
- COM
ms.assetid: 3fbaa77a-be43-4fce-af67-1826ee101799
description: "Last modified: March 09, 2015"
---

# SPropProblemArray

  
  
**Applies to**: Outlook 
  
Contains an array of one or more [SPropProblem](spropproblem.md) structures. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macros:  <br/> |[CbNewSPropProblemArray](cbnewspropproblemarray.md) <br/> [CbSPropProblemArray](cbspropproblemarray.md) <br/> [SizedSPropProblemArray](sizedspropproblemarray.md) <br/> |
   
```cpp
typedef struct _SPropProblemArray
{
  ULONG cProblem;
  SPropProblem aProblem[MAPI_DIM];
} SPropProblemArray, FAR *LPSPropProblemArray;

```

## Members

 **cProblem**
  
> Count of [SPropProblem](spropproblem.md) structures in the array indicated by the **aProblem** member. 
    
 **aProblem**
  
> Array of **SPropProblem** structures, each describing a property error. 
    
## Remarks

For more information about how the **SPropProblem** and **SPropProblemArray** structures work with errors related to properties, see [MAPI Named Properties](mapi-named-properties.md). 
  
## See also



[SCODE](scode.md)
  
[SPropProblem](spropproblem.md)


[MAPI Structures](mapi-structures.md)

