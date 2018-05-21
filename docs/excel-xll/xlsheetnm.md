---
title: "xlSheetNm"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlSheetNm
keywords:
- xlsheetnm function [excel 2007]
 
localization_priority: Normal
ms.assetid: bcb16207-5499-4474-b006-51ccde1002d7
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlSheetNm

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Returns the name of a worksheet or macro sheet from its internal sheet ID contained within an external reference, or the name of the current sheet if passed an internal reference.
  
```cs
Excel12(xlSheetNm, LPXLOPER12 pxRes, 1, LPXLOPER12 pxExtref);
```

## Parameters

 _pxExtref_ ( **xltypeRef** or **xltypeSRef**)
  
A reference to the sheet whose name you want.
  
If you are passing an external reference ( **xltypeRef**) it need only contain the ID of the sheet. The data structures that describe the cells on the worksheet are ignored and do not need to be provided. If the ID is set to zero, **xlSheetNm** returns the name of the current sheet. 
  
If you are passing an internal reference ( **xltypeSef**), **xlSheetNm** returns the name of the current sheet. 
  
## Property value/Return value

Returns the name of the sheet ( **xltypeStr**) in the form  `[Book1]Sheet1`.
  
## Example

The following example displays the name of the sheet from which the function was called. The function works correctly only if called from a macro sheet while executing an XLM command macro. This is because it calls **xlcAlert**, which only commands can do, and it needs to be called from a sheet rather than a dialog box, menu, or command bar in order for **xlfCaller** to return a reference. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI xlSheetNmExample(void)
{
   XLOPER12 xRes, xSheetName;
   Excel12(xlfCaller, &xRes, 0);
   Excel12(xlSheetNm, &xSheetName, 1, (LPXLOPER12)&xRes);
   Excel12(xlcAlert, 0, 1, (LPXLOPER12)&xSheetName);
   Excel12(xlFree, 0, 1, (LPXLOPER12)&xSheetName);
   return 1;
}
```

## See also



[xlSheetId](xlsheetid.md)


[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

