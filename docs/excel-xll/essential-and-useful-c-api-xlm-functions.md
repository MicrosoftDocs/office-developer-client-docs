---
title: "Essential and Useful C API XLM Functions"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- functions [excel 2007], c api xlm
 
localization_priority: Normal
ms.assetid: dc80cb3d-0d7e-4cb9-9870-3acc84eeca82
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Essential and Useful C API XLM Functions

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
The functions described in this section are Microsoft Excel callback functions that are particularly useful to DLL and XLL developers. Of these, the **xlfRegister** function is essential for XLLs and DLLs that want to register their functions and commands so that they can be called directly from Excel. The functions **xlfUnregister** and **xlfSetName** are used in combination to unregister DLL and XLL functions and commands. 
  
Many more functions are exposed by Excel via the C API that are useful when you are developing XLLs. They correspond to the Excel worksheet functions and functions and commands that are available from XLM macro sheets.
  
## In This Section

[xlfCaller](xlfcaller.md)
  
[xlfEvaluate](xlfevaluate.md)
  
[xlfGetDef](xlfgetdef.md)
  
[xlfGetName](xlfgetname.md)
  
[xlfRegister (Form 1)](xlfregister-form-1.md)
  
[xlfRegister (Form 2)](xlfregister-form-2.md)
  
[xlfRegisterId](xlfregisterid.md)
  
[xlfUnregister (Form 1)](xlfunregister-form-1.md)
  
[xlfUnregister (Form 2)](xlfunregister-form-2.md)
  
[xlfSetName](xlfsetname.md)
  

