---
title: "xlSheetId"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlSheetId
keywords:
- xlsheetid function [excel 2007]
 
localization_priority: Normal
ms.assetid: cb32059c-b899-49cf-8028-ff828998ab75
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlSheetId

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Finds the sheet ID of a named sheet in order to construct external references.
  
```cs
Excel12(xlSheetId, LPXLOPER12 pxRes, 1, LPXLOPER12 pxSheetName);
```

## Parameters

 _pxSheetName_ ( **xltypeStr**)
  
(Optional). The name of the book and sheet you want to find out about. If omitted, the **xlSheetId** function returns the sheet ID of the active (front) sheet. 
  
## Return value

Returns the sheet ID in  _pxRes-\>val.mref.idSheet_. 
  
> [!NOTE]
> The  _pxRes-\>val.mref.lpmref_ array pointer is set to NULL after this call so that there is no need to call **xlFree** to release the memory that this type normally contains, although it is completely safe to do so. 
  
## Remarks

The workbook containing the specified sheet must be open to use this function. There is no way to construct a reference to an unopened workbook from a DLL. For more information about using **xlSheetId** to construct references, see [Memory Management in Excel](memory-management-in-excel.md) for examples of **xltypeRef** construction. 
  
## Example

 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI xlSheetIdExample(void)
{       
   XLOPER12 xSheetName, xRes;
   xSheetName.xltype = xltypeStr;
   xSheetName.val.str = L"\022[BOOK1.XLSX]Sheet1";
   Excel12(xlSheetId, &amp;xRes, 1, (LPXLOPER12)&amp;xSheetName);
   Excel12f(xlcAlert, 0, 1, TempNum12(xRes.val.mref.idSheet));
   Excel12(xlFree, 0, 1, (LPXLOPER12)&amp;xRes);
   return 1;
}
```

## See also

#### Reference

[xlSheetNm](xlsheetnm.md)
#### Concepts

[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

