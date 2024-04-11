---
title: "SizedADRLIST"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SizedADRLIST
api_type:
- COM
ms.assetid: 5c64d74a-83a7-4122-b1d1-fcca0f4a6cdb
description: "Defines an ADRLIST structure with the specified name that contains a specified number of ADRENTRY structures."
---

# SizedADRLIST

**Applies to**: Outlook 2013 | Outlook 2016 
  
Defines an [ADRLIST](adrlist.md) structure with the specified name that contains a specified number of [ADRENTRY](adrentry.md) structures. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**ADRLIST** <br/> |
   
```cpp
SizedADRLIST (_centries,_name)
```

## Parameters

__centries_
  
> Count of **ADRENTRY** structures to be included in the new **ADRLIST** structure. 
    
__name_
  
> Name for the new **ADRLIST** structure. 
    
## Remarks

The **SizedADRLIST** macro lets you define a recipient list that has explicit bounds when array length requirements are known. The following code shows how to cast the result of the **SizedADRLIST** macro to an **ADRLIST** structure pointer: 
  
```cpp
lpADRList = (LPADRLIST) &SizedADRList;
```

## See also

- [ADRLIST](adrlist.md)
- [ADRENTRY](adrentry.md)
- [Macros Related to Structures](macros-related-to-structures.md)

