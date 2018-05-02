---
title: "UFromSz"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.UFromSz
api_type:
- COM
ms.assetid: 4a67faa2-8c2e-49a7-8c92-690a0a65c8f7
description: "Last modified: March 09, 2015"
---

# UFromSz

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Converts a null-terminated string of decimal digits into an unsigned integer. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```
UINT UFromSz(
  LPCSTR lpsz
);
```

## Parameters

 _lpsz_
  
> [in] Pointer to the null-terminated string to be converted. The  _lpsz_ parameter must not exceed 65536 characters. 
    
## Return value

 **UFromSz** returns an unsigned integer. If the string does not begin with at least one decimal digit, zero is returned. 
  
## Remarks

The **UFromSz** function stops converting when it reaches the first character in the string that is not a decimal digit. For example, given the string "55", **UFromSz** returns the integer value 55. Given the string "5a5b", the function returns the integer value 5. Given the string "a5b5", **UFromSz** returns zero. 
  
 **UFromSz** is sensitive to diacritical differences. Strings in the Unicode and DBCS formats are supported. The length limit on  _lpsz_ is in characters, not necessarily bytes. 
  

