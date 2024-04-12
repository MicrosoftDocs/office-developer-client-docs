---
title: "xlfUnregister (Form 2)"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlfUnregister (Form 2)
keywords:
- xlfunregister [excel 2007]
ms.localizationpriority: medium
ms.assetid: 39c6eba7-ba41-4e7b-9a28-2b662378ff5a

---

# xlfUnregister (Form 2)

**Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
Can be called from a DLL or XLL command that has itself been called by Microsoft Excel. This is equivalent to calling **UNREGISTER** from an Excel XLM macro sheet.
  
**xlfUnregister** can be called in two forms:
  
- Form 1: Unregisters an individual command or function.

- Form 2: Unloads and deactivates an XLL.

Called in Form 2, this function forces a DLL or code resource to be unloaded completely. It unregisters all of the functions in a DLL, even if they are currently in use by another macro, no matter what the use count. This function calls **xlAutoClose**, and then unregisters all the functions in the DLL.
  
```cs
Excel12(xlfUnregister, LPXLOPER12 pxRes, 1, LPXLOPER12 pxModuleText);
```

## Parameters

_pxModuleText_ (**xltypeStr**)
  
The name of the DLL.
  
## Property value/Return value

If successful, returns **TRUE** (**xltypeBool**). If unsuccessful, returns **FALSE**.
  
## Remarks

> [!NOTE]
> Do not call this form of the function from your implementation of the [xlAutoClose](xlautoclose.md) in an attempt to unregister all of the DLL's resources with one simple function call. This leads to recursive calling of **xlAutoClose** and a stack overflow.
  
### Remember to delete names

If you specified the _pxFunctionText_ argument to **xlfRegister**, when registering the DLL's functions and commands, you must explicitly delete the names by calling **xlfSetName** for each one, omitting the second argument so that the function no longer appears in the Function Wizard. For more information, see [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md).
  
## See also

- [xlfRegister (Form 1)](xlfregister-form-1.md)
- [xlfRegisterId](xlfregisterid.md)
- [xlfUnregister (Form 1)](xlfunregister-form-1.md)
- [Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)
