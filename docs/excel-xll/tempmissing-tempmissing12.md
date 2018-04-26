---
title: "TempMissing/TempMissing12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- TempMissing
- TempMissing12
keywords:
- tempmissing function [excel 2007],TempMissing12 function [Excel 2007]
 
localization_priority: Normal
ms.assetid: d9cb6afc-1fbb-45d6-88e5-84eba3af3c60
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# TempMissing/TempMissing12

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Framework library function that creates a temporary **XLOPER**/ **XLOPER12** of type **xltypeMissing**.
  
```cs
LPXLOPER TempMissing(void);
LPXLOPER12 TempMissing12(void);
```

## Parameters

This function takes no parameters.
  
## Return value

Returns a pointer to an **xltypeMissing** **XLOPER**/ **XLOPER12**.
  
## Example

This example uses **TempMissing12** to provide three missing arguments to **xlcWorkspace** followed by a **Boolean** **FALSE** to suppress the display of worksheet scroll bars. The first three arguments correspond to other workspace settings which are unaffected. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI TempMissingExample(void)
{
   XLOPER12 xBool;
   xBool.xltype = xltypeBool;
   xBool.val.xbool = 0;
   Excel12f(xlcWorkspace, 0, 4, TempMissing12(), TempMissing12(),
      TempMissing12(), (LPXLOPER12)&amp;xBool);
   return 1;
}
```

## See also

#### Concepts

[Functions in the Framework Library](functions-in-the-framework-library.md)

