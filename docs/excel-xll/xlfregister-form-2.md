---
title: "xlfRegister (Form 2)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlfRegister
keywords:
- xlfregister function [excel 2007]
 
localization_priority: Normal
ms.assetid: 3ebbd775-f3d2-4ba7-8835-a5b38ad2267a
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlfRegister (Form 2)

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Can be called from a DLL or XLL command that has itself been called by Microsoft Excel. This is equivalent to calling **REGISTER** from an Excel XLM macro sheet. 
  
The **xlfRegister** function can be called in two forms: 
  
- [xlfRegister (Form 1)](xlfregister-form-1.md): Registers an individual command or function.
    
- xlfRegister (Form 2): Loads and activates an XLL.
    
Called in Form 2, this function can only be used to load and activate an XLL containing an [xlAutoOpen](xlautoopen.md) procedure. 
  
```cs
Excel12(xlfRegister, LPXLOPER12 pxRes, 1, LPXLOPER12 pxModuleText);
```

## Parameters

 _pxModuleText_ (**xltypeStr**)
  
The name of the DLL to be loaded and activated.
  
## Property value/Return value

If successful, this returns the name of the DLL (**xltypeStr**). Otherwise it returns a #VALUE! error.
  
## See also



[Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)

