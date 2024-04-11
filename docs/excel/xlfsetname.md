---
title: "xlfSetName"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlfSetName
keywords:
- xlfsetname function [excel 2007]
ms.localizationpriority: medium
ms.assetid: ea7fd713-7c1b-4648-a609-3334f595c61a

---

# xlfSetName

**Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
Used to create and delete defined names associated with the DLL.
  
```cs
Excel12(xlfSetName, LPXLOPER12 pxRes, 2, LPXLOPER12 pxNameText, LPXLOPER12 pxNameDefinition);
```

## Parameters

_pxNameText_ (**xltypeStr**)
  
The name of the range, which should conform to the usual limitations in Microsoft Excel on valid names.
  
_pxNameDefinition_ (**xltypeStr**, **xltypeNum**, **xltypeBool**, **xltypeErr**, **xltypeMulti**, **xltypeSRef**, **xltypeRef**, or **xltypeInt**)
  
(Optional). The value, set of values, cell, or range of cells that _pxNameText_ is defined as. If omitted, the name is deleted.
  
## Property value/Return value

_pxRes_ (**xltypeBool** or **xltypeErr**)
  
TRUE if the operation succeeded or FALSE if the name could not be created or deleted. Returns #VALUE! if one or more of the arguments was invalid.
  
## Remarks

When a function or command is registered using **xlfRegister** with a valid _pxFunctionText_ argument, Excel creates a name associated with the DLL resource. When your DLL is being unloaded, such names should be deleted using the [xlfSetName function](xlfsetname.md). However, due to a known issue in Excel, this deletion operation fails. For more information, see [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md).
  
### Example

See the code for the **xlAutoClose** function in `\SAMPLES\GENERIC\GENERIC.C`.
  
## See also

- [Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)
