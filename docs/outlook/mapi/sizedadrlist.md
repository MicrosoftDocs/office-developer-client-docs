---
title: "SizedADRLIST"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedADRLIST
api_type:
- COM
ms.assetid: 5c64d74a-83a7-4122-b1d1-fcca0f4a6cdb
description: "Last modified: March 09, 2015"
---

# SizedADRLIST

  
  
**Applies to**: Outlook 
  
Defines an [ADRLIST](adrlist.md) structure with the specified name that contains a specified number of [ADRENTRY](adrentry.md) structures. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**ADRLIST** <br/> |
   
```
SizedADRLIST (_centries,_name)
```

## Parameters

 __centries_
  
> Count of **ADRENTRY** structures to be included in the new **ADRLIST** structure. 
    
 __name_
  
> Name for the new **ADRLIST** structure. 
    
## Remarks

The **SizedADRLIST** macro lets you define a recipient list that has explicit bounds when array length requirements are known. The following code shows how to cast the result of the **SizedADRLIST** macro to an **ADRLIST** structure pointer: 
  
```
lpADRList = (LPADRLIST) &amp;SizedADRList;

```

## See also

#### Reference

[ADRLIST](adrlist.md)
  
[ADRENTRY](adrentry.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

