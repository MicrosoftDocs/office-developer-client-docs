---
title: "xlDefineBinaryName"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlDefineBinaryName
keywords:
- xldefinebinaryname function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: e3e8f91b-cc31-4f09-9941-f950ae96820a

---

# xlDefineBinaryName

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Used to allocate persistent storage for an **xltypeBigData** **XLOPER**/ **XLOPER12**. Data with a defined binary name is saved with the workbook, and can be accessed by name at any time. For more information, see "Binary Name Scope Limitation" in [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md).
  
```cs
Excel12(xlDefineBinaryName, 0, 2, LPXLOPER12 pxName, LPXLOPER12 pxData);
```

## Parameters

 _pxName_ (**xltypeStr**)
  
A string specifying the name of the data. The string is subject to the same naming restrictions as defined names.
  
 _pxData_ (**xltypeBigData**)
  
Bigdata structure specifying the data to be stored. When you call this function, the **lpbData** member of the **bigdata** structure should point to the data for which the name is being defined, and the **cbData** member should contain the length of the data in bytes. 
  
If the  _pxData_ argument is not specified (**xltypeMissing**), the named allocation specified by  _pxName_ is deleted. 
  
## See also



[xlGetBinaryName](xlgetbinaryname.md)


[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)
  
[Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md)

