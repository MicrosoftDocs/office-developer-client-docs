---
title: "TempStrConst/TempStr12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- TempStr12
- TempStrConst
keywords:
- tempstr12 function [excel 2007],TempStrConst function [Excel 2007]
 
ms.localizationpriority: medium
ms.assetid: faf4ee4e-8d33-4cb3-ae16-5648a837ee4f
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# TempStrConst/TempStr12

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework library function that creates a temporary **XLOPER/XLOPER12** that contains an **xltypeStr** string, taking a null-terminated source string as input. The function allocates a new memory buffer and copies the passed-in string into it. The input string is not altered and so is declared as **const**.
  
```cs
LPXLOPER TempStrConst(const LPSTR str);
LPXLOPER12 TempStr12(const XCHAR* lpstr);
```

## Parameters

 _str_
  
A pointer to the null-terminated source string. In the case of **XLOPER**s, TempStrConst truncates strings that are longer than 255 bytes. In the case of **XLOPER12**s, TempStr12Const truncates strings that are longer than 32,767 Unicode characters.
  
## Return value

Returns an **xltypeStr** string containing a copy of the passed-in string buffer. 
  
## Remarks

Note that the **XLOPER** string Framework function, **TempStr**, behaves differently and tries to overwrite the first character of the supplied string with the subsequent string's length. This is not always a safe thing to do: Microsoft Excel might crash if passed a read-only string. This way of creating temporary strings is now deprecated in favor of the way in which both **TempStrConst** and **TempStr12** work. Therefore the first character of the input string is treated as the start of the string, that is, not as a length character or as a space for a length character. You should not pass strings that have a length character encoded at the start, as the consequences could be unpredictable. 
  
## Example

This example uses the **TempStr12** function to create a string for a message box. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI TempStrExample(void)
{
   Excel12f(xlcAlert, 0, 1, TempStr12Const(L"Made it!"));
   return 1;
}
```

## See also



[Functions in the Framework Library](functions-in-the-framework-library.md)

