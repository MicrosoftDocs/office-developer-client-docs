---
title: "TempActiveCell/TempActiveCell12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- TempActiveCell
- TempActiveCell12
keywords:
- tempactivecell12 function [excel 2007],TempActiveCell function [Excel 2007]
 
localization_priority: Normal
ms.assetid: ac5a200d-32d5-4313-9a6d-d730032aaf10
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# TempActiveCell/TempActiveCell12

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Framework library functions that create a temporary **XLOPER**/ **XLOPER12** containing an external reference to a cell on the active sheet. 
  
```cs
LPXLOPER TempActiveCell(WORD row, BYTE col);
LPXLOPER12 TempActiveCell12(RW row, COL co);
```

## Parameters

 _row_
  
The row to be referenced. Row arguments are zero-based so that row 1 is passed as 0. In Microsoft Office Excel 2003 and earlier versions, and starting in Excel 2007 running a workbook in compatibility mode, the maximum value is 65,535 = 2^16 - 1 and is the maximum value that can be taken by a WORD integer. Starting in Excel 2007 running a workbook, the maximum value is 1,048,575 = 2^20 - 1. RW is defined as a 32-bit signed integer in XLCALL.H.
  
 _col_
  
The column to be referenced. This is zero-based so that column A is passed as 0. In Excel 2003 and earlier versions, and starting in Excel 2007 running a workbook in compatibility mode, the maximum value is 255 = 2^8 - 1 and is the maximum value that can be taken by a BYTE integer. Starting in Excel 2007 running a workbook, the maximum value is 16,383 = 2^14 - 1. COL is defined as a 32-bit signed integer in XLCALL.H.
  
## Return value

Returns an **xltypeRef** external reference to the cell passed in. 
  
## Example

The following example uses **TempActiveCell12** to display the contents of B94 on the active sheet. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI TempActiveCellExample(void)
{
   Excel12f(xlcAlert, 0, 1, TempActiveCell12(93,1));
   return 1;
}
```

## See also

#### Concepts

[Functions in the Framework Library](functions-in-the-framework-library.md)

