---
title: "xlfRegisterId"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlfRegisterId
keywords:
- xlfregisterid function [excel 2007]
localization_priority: Normal
ms.assetid: d34cf20c-a5cd-45fb-9dcb-d49eac2d99dd
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlfRegisterId

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Can be called from a DLL that has itself been called by Microsoft Excel. If a function is already registered, it returns the existing register ID for that function without reregistering it. If a function is not yet registered, it registers it and returns the resulting register ID.
  
```cs
Excel12(xlfRegisterId, LPXLOPER12 pxRes, 3,     LPXLOPER12 pxModuleText, LPXLOPER12 pxProcedure, LPXLOPER12 pxTypeText);
```

## Parameters

_pxModuleText_ (**xltypeStr**)
  
The name of the DLL containing the function.
  
_pxProcedure_ (**xltypeStr** or **xltypeNum**)
  
If a string, the name of the function to call. If a number, the ordinal export number of the function to call. For clarity and robustness, always use the string form.
  
_pxTypeText_ (**xltypeStr**)
  
An optional string specifying the types of all the arguments to the function and the type of the return value of the function. For more information, see the "Remarks" section. This argument can be omitted for a stand-alone DLL (XLL) defining **xlAutoRegister**.
  
## Property value/Return value

Returns the register ID of the function (**xltypeNum**), which can be used in subsequent calls to **xlfUnregister**.
  
## Remarks

This function is useful when you do not want to worry about maintaining a register ID, but you need one later for unregistering. It is also useful for assigning to menus, tools, and buttons when the function you want to assign is in a DLL.
  
Where a DLL or XLL function has been registered with a valid  _pxFunctionText_ argument having been supplied to **xlfRegister**, its register ID can also be obtained by passing the  _pxFunctionText_ to the function **xlfEvaluate**.
  
## See also

- [REGISTER](xlfregister-form-1.md)
- [UNREGISTER](xlfunregister-form-1.md)
- [Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)

