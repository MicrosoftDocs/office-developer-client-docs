---
title: "TempActiveRef/TempActiveRef12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- TempActiveRef
- TempActiveRef12
keywords:
- tempactiveref function [excel 2007],TempActiveRef12 function [Excel 2007]
 
localization_priority: Normal
ms.assetid: 7c69d15a-294b-4545-983b-720409001e0e
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# TempActiveRef/TempActiveRef12

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Framework library function that creates a temporary **XLOPER**/ **XLOPER12** containing an external reference to rectangular block of cells on the active sheet. 
  
```cs
LPXLOPER TempActiveRef(WORD rwFirst, WORD rwLast, BYTE colFirst, BYTE colLast);
LPXLOPER12 TempActiveRef12(ROW rwFirst, ROW rwLast, COL colFirst, COL colLast);
```

## Parameters

 _rwFirst_
  
The starting row of the reference.
  
 _rwLast_
  
The ending row of the reference.
  
Row arguments are zero-based so that row 1 is passed as 0. In Microsoft Office Excel 2003 and earlier versions, and starting in Excel 2007 running a workbook in compatibility mode, the maximum value is 65,535 = 2^16 - 1 and is the maximum value that can be taken by a WORD integer. Starting in Excel 2007 running a workbook, the maximum value is 1,048,575 = 2^20 - 1. RW is defined as a 32-bit signed integer in XLCALL.H.
  
 _colFirst_
  
The starting column number of the reference.
  
 _colLast_
  
The ending column number of the reference.
  
Column arguments are zero-based so that column A is passed as 0. In Excel 2003 and earlier versions, and starting in Excel 2007 running a workbook in compatibility mode, the maximum value is 255 = 2^8 - 1 and is the maximum value that can be taken by a BYTE integer. Starting in Excel 2007 running a workbook, the maximum value is 16,383 = 2^14 - 1. COL is defined as a 32-bit signed integer in XLCALL.H.
  
## Return value

Returns an **xltypeRef** external reference to rectangular block of cells passed in. 
  
## Example

This example uses the **TempActiveRef12** function to select cells A105:C110. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI TempActiveRefExample(void)
{
    Excel12f(xlcSelect, 0, 1, TempActiveRef12(104, 109, 0, 2));
    return 1;
}
```

## See also

#### Concepts

[Functions in the Framework Library](functions-in-the-framework-library.md)

