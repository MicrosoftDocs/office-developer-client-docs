---
title: "TempNum/TempNum12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- TempNum
- TempNum12
keywords:
- tempnum12 function [excel 2007],TempNum function [Excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 5b74d618-db3a-4d84-bd17-4fee7ae3b51e
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# TempNum/TempNum12

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework library function that creates a temporary **XLOPER**/ **XLOPER12** containing a Microsoft Excel worksheet number (an IEEE 8-byte double). 
  
```cs
LPXLOPER TempNum(double d);
LPXLOPER12 TempNum12(double d);
```

## Parameters

 _d_ (**double**)
  
The intended value. Note that IEEE sub-normal numbers are not currently supported and are rounded to zero. Negative infinity is supported.
  
## Return value

Returns a numeric **xltypeNum** containing the value passed in or zero if the passed in value was sub-normal. 
  
## Example

This example uses the **TempNum12** function to pass an argument to **xlfGetWorkspace**.
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI TempNumExample(void)
{
   XLOPER12 xRes;
   Excel12f(xlfGetWorkspace, &xRes, 1, TempNum12(44));
   Excel12f(xlFree, 0, 1, (LPXLOPER12)&xRes);
   return 1;
}
```

## See also



[Functions in the Framework Library](functions-in-the-framework-library.md)

