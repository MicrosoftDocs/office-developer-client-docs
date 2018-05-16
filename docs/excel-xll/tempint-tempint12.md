---
title: "TempInt/TempInt12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- TempInt
- TempInt12
keywords:
- tempint12 function [excel 2007],TempInt function [Excel 2007]
 
localization_priority: Normal
ms.assetid: 86d690b8-caca-450d-93f7-69ca4cd1a6e0
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# TempInt/TempInt12

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework library function that creates a temporary **XLOPER**/ **XLOPER12** that contains an integer. 
  
```cs
LPXLOPER TempInt(short int i);
LPXLOPER12 TempInt12(int i);
```

## Parameters

 _i_
  
The intended integer value. Note that the **XLOPER** integer is a signed 16-bit integer (short int), whereas the **XLOPER12** integer is a signed 32-bit integer ([long] int). 
  
## Return value

Returns an **xltypeInt** integer containing the value passed in. 
  
## Example

This example uses the **TempInt12** function to pass an argument to **xlfGetWorkspace**.
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI TempIntExample(void)
{
    XLOPER12 xRes;
    Excel12f(xlfGetWorkspace, (LPXLOPER12)&amp;xRes, 1, TempInt12(44));
    Excel12f(xlFree, 0, 1, (LPXLOPER12)&amp;xRes);
    return 1;
}
```

## See also

#### Concepts

[Functions in the Framework Library](functions-in-the-framework-library.md)

