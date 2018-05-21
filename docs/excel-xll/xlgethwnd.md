---
title: "xlGetHwnd"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlGetHwnd
keywords:
- xlgethwnd function [excel 2007]
 
localization_priority: Normal
ms.assetid: be33b097-812b-4f5c-81be-4d9673e95b0b
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlGetHwnd

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Returns the window handle of the top-level Microsoft Excel window.
  
```cs
Excel4(xlGetHwnd, LPXLOPER pxRes, 0); /* returns low part only */
Excel12(xlGetHwnd, LPXLOPER12 pxRes, 0); /* returns full handle */
```

## Parameters

This function has no arguments.
  
## Property value/Return value

Contains the window handle ( **xltypeInt**) in the **val.w** field. 
  
## Remarks

This function is useful for writing Windows API code.
  
When you call this function using [Excel4](excel4-excel12.md) or [Excel4v](excel4v-excel12v.md), the returned XLOPER integer variable is a signed 16-bit short int. This is only capable of containing the low 16 bits of the 32-bit Windows handle. To find the high part, your code must iterate through all open windows looking for a match with the low part. Starting in Excel 2007, the integer variable of the **XLOPER12** is a signed 32-bit int and therefore contains the entire handle, removing the need to iterate all open windows. 
  
### Example

See the code for the [fShowDialog function](fshowdialog.md) in  `SAMPLES\GENERIC\GENERIC.C`.
  
## See also



[xlGetInst](xlgetinst.md)


[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

