---
title: "UlFromSzHex"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.UlFromSzHex
api_type:
- COM
ms.assetid: e2d6b6bf-f96d-460c-859a-21961ac9237c
description: "Last modified: March 09, 2015"
---

# UlFromSzHex

  
  
**Applies to**: Outlook 
  
Converts a null-terminated string of hexadecimal digits into an unsigned long integer. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
ULONG UlFromSzHex(
LPCSTR lpsz
);
```

## Parameters

 _lpsz_
  
> [in] Pointer to the null-terminated string to be converted. The  _lpsz_ parameter must not exceed 65536 characters. 
    
## Return value

 **UlFromSzHex** returns an unsigned long integer. If the string does not begin with at least one hexadecimal digit, zero is returned. 
  
## Remarks

The **UlFromSzHex** function stops converting when it reaches the first character in the string that is not a hexadecimal digit. For example, given the string "5a", **UlFromSzHex** returns the integer value 90. Given the string "5g5h", the function returns the integer value 5. Given the string "g5h5", **UlFromSzHex** returns zero. 
  
 **UlFromSzHex** is sensitive to diacritical differences but allows both 'a' through 'f' and 'A' through 'F' for hexadecimal digits. Strings in the Unicode and DBCS formats are supported. The length limit on  _lpsz_ is in characters, not necessarily bytes. 
  

