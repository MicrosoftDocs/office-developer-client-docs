---
title: "FtAddFt"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FtAddFt
api_type:
- COM
ms.assetid: 341ad06b-1caa-49bb-b859-cb512f6fb55d
description: "Adds one unsigned 64-bit integer to another."
---

# FtAddFt

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Adds one unsigned 64-bit integer to another.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
FILETIME FtAddFt(
  FILETIME Addend1,
  FILETIME Addend2
);
```

## Parameters

 _Addend1_
  
> [in] A [FILETIME](filetime.md) structure that contains the first unsigned 64-bit integer to be added. 
    
 _Addend2_
  
> [in] A **FILETIME** structure that contains the second unsigned 64-bit integer to be added. 
    
## Return value

The **FtAddFt** function returns a **FILETIME** structure that contains the sum of the two integers. The two input parameters remain unchanged. 
  

