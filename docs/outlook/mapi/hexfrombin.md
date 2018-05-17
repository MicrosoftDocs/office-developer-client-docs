---
title: "HexFromBin"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.HexFromBin
api_type:
- COM
ms.assetid: 12b95657-1926-4a24-be63-40305ea6f990
description: "Last modified: March 09, 2015"
---

# HexFromBin

  
  
**Applies to**: Outlook 
  
Converts a binary number into a string representation of a hexadecimal number. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```
void HexFromBin(
  LPBYTE pb,
  int cb,
  LPSTR sz
);
```

## Parameters

 _pb_
  
> [in] Pointer to the binary data to be converted. 
    
 _cb_
  
> [in] Size, in bytes, of the binary data pointed to by the  _pb_ parameter. 
    
 _sz_
  
> [out] Pointer to a null-terminated ASCII string representing the binary data in hexadecimal digits.
    
## Return value

None.
  
## Remarks

The **HexFromBin** function takes a pointer to a unit of binary data whose size is indicated by the  _cb_ parameter. It returns in the  _sz_ string, within (2*  _cb_)+1 bytes of memory, a representation of this binary information in hexadecimal numbers. If the byte value is decimal 10, for example, the hexadecimal string will be 0A, so one byte converts to two bytes in the string. 
  

