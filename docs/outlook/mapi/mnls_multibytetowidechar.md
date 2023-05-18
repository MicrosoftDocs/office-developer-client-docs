---
title: "MNLS_MultiByteToWideChar"
description: "MNLS_MultiByteToWideChar maps a character string to a UTF-16 (wide character) string, which is not necessarily from a multibyte character set."
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 065d78bf-4c9c-48dd-b1f1-b4e59f3f1243
---

# MNLS_MultiByteToWideChar

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Similar to **MultiByteToWideChar**, which maps a character string to a UTF-16 (wide character) string. The character string is not necessarily from a multibyte character set.
  
```cpp
int MNLS_MultiByteToWideChar(
  UINT uCodePage,
  DWORD dwFlags,
  LPCSTR lpMultiByteStr,
  int cchMultiByte,
  LPWSTR lpWideCharStr,
  int cchWideChar);
```

## Parameters

 _uCodePage_
  
> [in] Code page to use in performing the conversion.
    
 _dwFlags_
  
> [in] Flags indicating the conversion type.
    
 _lpMultiByteStr_
  
> [in] Pointer to the character string to convert.
    
 _cchMultiByte_
  
> [in] Size, in bytes, of the string indicated by the  _lpMultiByteStr_ parameter. 
    
 _lpWideCharStr_
  
> [out] Optional. Pointer to a buffer that receives the converted string.
    
 _cchWideChar_
  
> [in] Size, in characters, of the buffer indicated by  _lpWideCharStr_.
    
## Return value

Returns the number of characters written to the buffer indicated by  _lpWideCharStr_ if successful. 
  
## Remarks

This function wraps the **MultiByteToWideChar** function. For more information, see [MultiByteToWideChar](https://msdn.microsoft.com/library/dd319072%28VS.85%29.aspx).
  

