---
title: "xlGetBinaryName"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- xlGetBinaryName
keywords:
- xlgetbinaryname function [excel 2007]
 
localization_priority: Normal
ms.assetid: 66af3f78-65b5-42e0-82f9-ffd639d41751
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlGetBinaryName

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Used to return a handle for data saved by the [xlDefineBinaryName function](xldefinebinaryname.md). Data with a defined binary name is saved with the workbook and can be accessed by name at any time. For more information, see "Binary name Scope Limitation" in [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md).
  
```cs
Excel12(xlGetBinaryName, LPXLOPER12 pxRes, 1, LPXLOPER12 pxName);
```

## Parameters

 _pxRes_ ( **xltypeBigData** or **xltypeErr**)
  
Bigdata structure specifying the retrieved data or an error is the data could not be retrieved or the name is not defined. When the function returns, the **hdata** member of the **XLOPER**/ **XLOPER12** contains a handle for the named data.  _pxRes_ should be freed in a call to **xlFree** when no longer required. 
  
 _pxName_ ( **xltypeStr**)
  
A string specifying the name of the data.
  
## Remarks

Microsoft Excel owns the memory handle returned in **hdata**. In Windows, the handle is a global memory handle (allocated by the **GlobalAlloc** function). 
  
## See also

#### Reference

[xlDefineBinaryName](xldefinebinaryname.md)
#### Concepts

[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

