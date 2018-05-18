---
title: "FtAdcFt"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2635a829-0f3a-49ed-a672-2f350a2cf979
description: "Last modified: March 09, 2015"
---

# FtAdcFt

  
  
**Applies to**: Outlook 
  
Adds one unsigned 64-bit integer to another, optionally using a carry flag.
  
|||
|:-----|:-----|
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
FILETIME FtAdcFt( 
  FILETIME ft1, 
  FILETIME ft2, 
  WORD FAR *pwCarry
);
```

## Parameters

 _ft1_
  
> [in] A [FILETIME](filetime.md) structure that contains the first unsigned 64-bit integer to be added. 
    
 _ft2_
  
> [in] A FILETIME structure that contains the second unsigned 64-bit integer to be added.
    
 _pwCarry_
  
> [in, out, optional] On input, a pointer to the incoming carry flag. On output, a pointer to the carry result for the addition. This parameter can be NULL if the carry result is not required.
    
## Return value

The **FtAdcFt** function returns a **FILETIME** structure that contains the sum of the two integers. The two input parameters remain unchanged. If **pwCarry** is non-NULL, it contains the carry result for the sum, either 0 or 1. 
  
## Remarks

The **FtAdcFt** function is identical to **FtAddFt** when  _pwCarry_ is NULL. If  _pwCarry_ is not NULL and points to 0, **FtAdcFt** returns the same **FILETIME** value that **FtAddFt** returns. 
  
## See also



[FtAddFt](ftaddft.md)

