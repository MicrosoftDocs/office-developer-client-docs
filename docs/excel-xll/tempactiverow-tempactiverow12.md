---
title: "TempActiveRow/TempActiveRow12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- TempActiveRow
- TempActiveRow12
keywords:
- tempactiverow function [excel 2007],TempActiveRow12 function [Excel 2007]
 
localization_priority: Normal
ms.assetid: cbb9181c-59b0-4133-a085-94a94ac3f229
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# TempActiveRow/TempActiveRow12

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Framework library functions that create a temporary **XLOPER**/ **XLOPER12** containing an external reference to an entire row on the active sheet. 
  
```cs
LPXLOPER TempActiveRow(WORD row);
LPXLOPER12 TempActiveRow12(ROW row);
```

## Parameters

 _row_
  
The row to be referenced. Row arguments are zero-based so that row 1 is passed as 0. In Microsoft Office Excel 2003 and earlier versions, and starting in Excel 2007 running a workbook in compatibility mode, the maximum value is 65,535 = 2^16 - 1 and is the maximum value that can be taken by a WORD integer. Starting in Excel 2007 running a workbook, the maximum value is 1,048,575 = 2^20 - 1. RW is defined as a 32-bit signed integer in XLCALL.H.
  
## Return value

Returns an **xltypeRef** external reference to row cells passed in. 
  
## Example

This example uses the **TempActiveRow12** function to select row 113. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI TempActiveRowExample(void)
{
   Excel12f(xlcSelect, 0, 1, TempActiveRow12(112));
   return 1;
}
```

## See also

#### Concepts

[Functions in the Framework Library](functions-in-the-framework-library.md)

