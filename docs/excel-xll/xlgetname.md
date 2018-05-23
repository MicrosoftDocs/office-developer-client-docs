---
title: "xlGetName"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlGetName
keywords:
- xlgetname function [excel 2007]
localization_priority: Normal
ms.assetid: 72dbebc0-7436-4771-8fbf-2b445341da65
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlGetName

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Returns the full path and file name of the DLL in the form of a string.
  
```cs
Excel12(xlGetName, LPXLOPER12 pxRes, 0);
```

## Parameters

This function has no arguments.
  
## Property value/Return value

Returns the path and file name (**xltypeStr**). 
  
## Example

`\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI xlGetNameExample(void)
{
    XLOPER12 xRes;
    Excel12(xlGetName, (LPXLOPER12)&xRes, 0);
    Excel12(xlcAlert, 0, 1, (LPXLOPER12)&xRes);
    Excel12(xlFree, 0, 1, (LPXLOPER12)&xRes);
    return 1;
}
```

## See also

- [C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

