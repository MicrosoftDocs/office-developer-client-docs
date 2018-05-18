---
title: "FBinFromHex"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FBinFromHex
api_type:
- COM
ms.assetid: 47e6c576-bd99-4410-8e41-7dd3159b23b7
description: "Last modified: March 09, 2015"
---

# FBinFromHex

  
  
**Applies to**: Outlook 
  
Converts a string representation of a hexadecimal number to binary data. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
BOOL FBinFromHex(
  LPSTR sz,
  LPBYTE pb
);
```

## Parameters

 _sz_
  
> [in] Pointer to the null-terminated ASCII string to be converted. It is not a Unicode string. Valid characters include the hexadecimal characters zero through nine and both uppercase and lowercase characters A through F.
    
 _pb_
  
> [out] Pointer to the returned binary number.
    
## Return value

TRUE 
  
> The string was successfully converted into a binary number. 
    
FALSE 
  
> The input string contains invalid ASCII hexadecimal characters.
    
## See also



[ScBinFromHexBounded](scbinfromhexbounded.md)

