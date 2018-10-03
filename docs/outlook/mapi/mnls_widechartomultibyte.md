---
title: "MNLS_WideCharToMultiByte"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f64cde12-7ed1-444f-8ca4-51cb3ea514cf
description: "Last modified: February 21, 2012"
---

# MNLS_WideCharToMultiByte

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This function is similar to **WideCharToMultiByte**, which maps a UTF-16 (wide character) string to a new character string. The new character string is not necessarily from a multibyte character set.
  
```cpp
int MNLS_WideCharToMultiByte(
  UINT uCodePage,
  DWORD dwFlags,
  LPCWSTR lpWideCharStr,
  int cchWideChar,
  LPSTR lpMultiByteStr,
  int cchMultiByte,
  LPCSTR lpDefaultChar,
  BOOL FAR *lpfUsedDefaultChar);
```

## Parameters

 _uCodePage_
  
> [in] Code page to use in performing the conversion.
    
 _dwFlags_
  
> [in] Flags indicating the conversion type.
    
 _lpWideCharStr_
  
> [in] Pointer to the Unicode string to convert.
    
 _cchWideChar_
  
> [in] Flags indicating the conversion type.
    
 _lpMultiByteStr_
  
> [out] Optional. Pointer to a buffer that receives the converted string.
    
 _cchMultiByte_
  
> [in] Size, in bytes, of the buffer indicated by  _lpMultiByteStr_.
    
 _lpDefaultChar_
  
> [in] Optional. Pointer to the character to use if a character cannot be represented in the specified code page.
    
 _lpfUsedDefaultChar_
  
> [out] Optional. Pointer to a flag that indicates if the function has used a default character in the conversion.
    
## Return value

Returns the number of bytes written to the buffer pointed to by  _lpMultiByteStr_ if successful. 
  
## Remarks

This function wraps the **WideCharToMultiByte** function. For more information, see [WideCharToMultiByte](https://msdn.microsoft.com/library/dd374130%28VS.85%29.aspx).
  
## See also



[WideCharToMultiByte](https://msdn.microsoft.com/library/dd374130%28VS.85%29.aspx)

