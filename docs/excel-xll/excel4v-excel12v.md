---
title: "Excel4v/Excel12v"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Excel12v
- Excel4v
keywords:
- excel12v function [excel 2007],Excel4v function [Excel 2007]
 
localization_priority: Normal
ms.assetid: e3e96b98-c5a7-4625-95b6-a1e2d09c6d3d
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Excel4v/Excel12v

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Calls an internal Microsoft Excel worksheet function, macro sheet function or command, or XLL-only special function or command, from within a DLL, XLL, or code resource.
  
All recent versions of Excel support **Excel4v**. Starting in Excel 2007, **Excel12v** is supported. 
  
These functions can be called only when Excel has passed control to the DLL or XLL. They can also be called when Excel has passed control indirectly via a call to Visual Basic for Applications (VBA). They cannot be called at any other time. For example, they cannot be called during calls to the DllMain function or other times when the operating system has called the DLL, or from a thread created by the DLL. 
  
The [Excel4 and Excel12](excel4-excel12.md) functions accept their arguments as a variable length list on the stack, whereas the **Excel4v** and **Excel12v** functions accept their arguments as an array. In all other respects, **Excel4** behaves the same as **Excel4v**, and **Excel12** behaves the same as **Excel12v**.
  
```cs
int _cdecl Excel4v(int iFunction, LPXLOPER pxRes, int iCount, LPXLOPER rgx[]);
int _cdecl Excel12v(int iFunction, LPXLOPER12 pxRes, int iCount, LPXLOPER12 rgx[]);
```

## Parameters

 _iFunction_ (**int**)
  
A number that indicates the command, function, or special function you want to call. For a list of valid  _iFunction_ values, see the following Remarks section. 
  
 _pxRes_ (**LPXLOPER** or **LPXLOPER12**)
  
A pointer to an **XLOPER** (in the case of **Excel4v**) or an **XLOPER12** (in the case of **Excel12v**) that will hold the result of the evaluated function.
  
 _iCount_ (**int**)
  
The number of subsequent arguments that will be passed to the function. In versions of Excel up to 2003 this can be any number from 0 through 30. Starting in Excel 2007, this can be any number from 0 through 255.
  
 _rgx_ (**LPXLOPER []** or **LPXLOPER12 []**)
  
An array that contains the arguments to the function. All arguments in the array must be pointers to **XLOPER** or **XLOPER12** values. 
  
## Return value

These functions return the same values as **Excel4** and **Excel12**.
  
## Remarks

These functions are useful where the number of arguments passed to the operator is variable. For example, **Excel4v** and **Excel12v** are useful when you register functions by using [xlfRegister](xlfregister-form-1.md) where the number of total arguments depends on the number of arguments taken by the function being registered. **Excel4v** and **Excel12v** are also useful when you write a wrapper function for **Excel4** or **Excel12**. In these cases, you need to convert a variable argument list, as would normally be supplied to **Excel4** or **Excel12**, to a single array argument of variable size to call back into Excel by using **Excel4v** or **Excel12v**.
  
### Example

For code examples, see the code for the **Excel** and **Excel12f** functions in the Excel 2010 XLL SDK, at the following location where you installed the SDK: 
  
Samples\Framewrk\Framewrk.c
  
## See also



[Excel4/Excel12](excel4-excel12.md)

