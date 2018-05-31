---
title: "TempBool/TempBool12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- TempBool
- TempBool12
keywords:
- tempbool function [excel 2007],TempBool12 function [Excel 2007]
 
localization_priority: Normal
ms.assetid: 0cf1fa58-416f-4692-a2e3-422473c19492
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# TempBool/TempBool12

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework library function that creates a temporary **XLOPER**/ **XLOPER12** containing **Boolean** **TRUE** or **FALSE**.
  
```cs
LPXLOPER TempBool(int b);
LPXLOPER12 TempBool12(int b);
```

## Parameters

 _b_ (**int**)
  
Use 0 to return **FALSE**; use any other value to return **TRUE**.
  
## Property value/Return value

Returns an **xltypeBool** **Boolean** containing the logical value passed in. 
  
## Example

The following example uses the **TempBool12** function to clear the status bar. Temporary memory is freed when the [Excel/Excel12f](excel-excel12f.md) function is called. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short int WINAPI TempBoolExample(void)
{
    Excel12f(xlcMessage, 0, 1, TempBool12(0));
    return 1;
}
```

## See also



[Functions in the Framework Library](functions-in-the-framework-library.md)

