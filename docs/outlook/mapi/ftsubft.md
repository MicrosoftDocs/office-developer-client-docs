---
title: "FtSubFt"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FtSubFt
api_type:
- COM
ms.assetid: 6619fc41-5518-44ce-85c1-6b0077ed5cb9
description: "Last modified: March 09, 2015"
---

# FtSubFt

  
  
**Applies to**: Outlook 
  
Subtracts one unsigned 64-bit integer from another. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```
FILETIME FtSubFt(
  FILETIME Minuend,
  FILETIME Subtrahend
);
```

## Parameters

 _Minuend_
  
> [in] A [FILETIME](filetime.md) structure that contains the unsigned 64-bit integer from which the value in the  _Subtrahend_ parameter is to be subtracted. 
    
 _Subtrahend_
  
> [in] A **FILETIME** structure that contains the unsigned 64-bit integer that is subtracted from the value indicated by the  _Minuend_ parameter. 
    
## Return value

The **FtSubFt** function returns a **FILETIME** structure that contains the result of the subtraction. The two input parameters remain unchanged. 
  

