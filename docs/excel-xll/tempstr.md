---
title: "TempStr"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- TempStr
keywords:
- tempstr function [excel 2007]
 
localization_priority: Normal
ms.assetid: b21b4868-babe-4255-9093-503172efa045
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# TempStr

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Deprecated Framework library function that creates a temporary **XLOPER** containing an **xltypeStr** byte string. It takes a null-terminated source string as input. It tries to overwrite the first character of the supplied string with the subsequent string's length. This is not always a safe thing to do: Microsoft Excel might crash if passed a read-only string. 
  
```cs
LPXLOPER TempStr(LPSTR str);
```

## Parameters

 _str_
  
A pointer to the null-terminated source string. **TempStr** truncates strings that are longer than 255 bytes. 
  
## Return value

Returns an **xltypeStr** string containing a pointer to the passed-in string buffer. 
  
## Remarks

This way of creating temporary strings is now deprecated in favor of the way in which both [TempStrConst and TempStr12](tempstrconst-tempstr12.md) work. These functions allocate a new memory buffer and copy the passed-in string into it. The input strings for **TempStrConst** and **TempStr12** are not altered and so are declared as **const**. In contrast, the input string to **TempStr** is altered and so cannot be declared as **const**. The first character of the input string is treated as space for a length character and is overwritten by this function.
  
## See also

#### Concepts

[Functions in the Framework Library](functions-in-the-framework-library.md)

