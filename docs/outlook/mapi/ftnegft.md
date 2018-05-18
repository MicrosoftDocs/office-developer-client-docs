---
title: "FtNegFt"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FtNegFt
api_type:
- COM
ms.assetid: 639a408c-aed1-456b-9f75-9d6fb8dcb33b
description: "Last modified: March 09, 2015"
---

# FtNegFt

  
  
**Applies to**: Outlook 
  
Computes the two's complement of an unsigned 64-bit integer. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
FILETIME FtNegFt(
  FILETIME ft
);
```

## Parameters

 _ft_
  
> [in] A [FILETIME](filetime.md) structure that contains the unsigned 64-bit integer for which to compute the two's complement. 
    
## Return value

The **FtNegFt** function returns a **FILETIME** structure that contains the two's complement of the integer. The input parameter remains unchanged. 
  

