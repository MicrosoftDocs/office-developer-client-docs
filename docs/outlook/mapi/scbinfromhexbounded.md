---
title: "ScBinFromHexBounded"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.ScBinFromHexBounded
api_type:
- COM
ms.assetid: edac715c-6edb-4b05-82e5-c08c3c7cb6d4
description: "Converts the specified portion of a string representation of a hexadecimal number into a binary number."
---

# ScBinFromHexBounded

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Converts the specified portion of a string representation of a hexadecimal number into a binary number. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE ScBinFromHexBounded(
  LPSTR sz,
  LPBYTE pb,
  ULONG cb
);
```

## Parameters

 _sz_
  
> [in] Pointer to the null-terminated string to be converted. Valid characters include the hexadecimal characters 0 through 9 and both uppercase and lowercase characters a through f.
    
 _pb_
  
> [out] Pointer to the returned binary number.
    
 _cb_
  
> [in] Size, in bytes, of the  _pb_ parameter. 
    
## Return value

S_OK
  
> Conversion was successful.
    
MAPI_E_CALL_FAILED
  
> Invalid characters were encountered.
    
## See also



[FBinFromHex](fbinfromhex.md)

