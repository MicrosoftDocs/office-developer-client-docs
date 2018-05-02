---
title: "SizedSSortOrderSet"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedSSortOrderSet
api_type:
- COM
ms.assetid: f0b9c2f4-7011-414d-8e6c-ab22893ef132
description: "Last modified: March 09, 2015"
---

# SizedSSortOrderSet

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Creates a named [SSortOrderSet](ssortorderset.md) structure that contains a specified number of sort orders. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**SSortOrderSet** <br/> |
   
```
SizedSSortOrderSet (_csort,_name)
```

## Parameters

 __csort_
  
> Count of sort orders to be included in the new structure.
    
 __name_
  
> Name for the new structure.
    
## Remarks

Use the **SizedSSortOrderSet** macro to create a sort order set with explicit bounds. 
  
To use the new structure that results from the **SizedSSortOrderSet** macro as a pointer to an **SSortOrderSet** structure, perform the following cast: 
  
```
lpSSortOrderSet = (LPSSortOrderSet) &amp;SizedSSortOrderSet;

```

## See also

#### Reference

[SSortOrderSet](ssortorderset.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

