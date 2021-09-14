---
title: "FtMulDw"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FtMulDw
api_type:
- COM
ms.assetid: e135ba67-97be-4ce0-a72e-93c49ed7d6e2
description: "Last modified: March 09, 2015"
---

# FtMulDw

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Multiplies an unsigned 64-bit integer by an unsigned 32-bit integer.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
FILETIME FtMulDw(
  DWORD Multiplier,
  FILETIME Multiplicand
);
```

## Parameters

 _Multiplier_
  
> [in] A double word that contains the unsigned 32-bit integer multiplier. 
    
 _Multiplicand_
  
> [in] A [FILETIME](filetime.md) structure that contains the unsigned 64-bit integer to be multiplied by the value in the  _Multiplier_ parameter. 
    
## Return value

The **FtMulDw** function returns a **FILETIME** structure that contains the product of the two integers. The two input parameters remain unchanged. 
  

