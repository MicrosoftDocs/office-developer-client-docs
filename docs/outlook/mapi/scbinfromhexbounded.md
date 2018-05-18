---
title: "ScBinFromHexBounded"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ScBinFromHexBounded
api_type:
- COM
ms.assetid: edac715c-6edb-4b05-82e5-c08c3c7cb6d4
description: "Last modified: March 09, 2015"
---

# ScBinFromHexBounded

  
  
**Applies to**: Outlook 
  
Converts the specified portion of a string representation of a hexadecimal number into a binary number. 
  
|||
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

#### Reference

[FBinFromHex](fbinfromhex.md)

