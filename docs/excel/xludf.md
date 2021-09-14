---
title: "xlUDF"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlUDF
keywords:
- xludf function [excel 2007]
ms.localizationpriority: medium
ms.assetid: b608b356-ca5c-47bb-9de8-9b7e2b3924dd
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlUDF

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Calls a user-defined function (UDF). This function allows a DLL to call Visual Basic for Applications (VBA) user-defined functions, XLM macro language functions, and registered functions contained in other add-ins.
  
```cs
Excel12(xlUDF, LPXLOPER12 pxRes, int iCount, LPXLOPER12 pxFnRef,
LPXLOPER12 pxArg1, ...);
```

## Parameters

_pxFnRef_ (**xltypeRef**, **xltypeSRef**, **xltypeStr** or **xltypeNum**)
  
The reference of the function you want to call. This can be a macro sheet cell reference, the registered name of the function as a string, or the register ID of the function. For XLL add-in functions registered using **xlfRegister** or **REGISTER** with the argument  _pxFunctionText_ supplied, the ID can be obtained by using **xlfEvaluate** to look up the name. 
  
_pxArg1, ..._
  
Zero or more arguments to the user-defined function. When you are calling this function in versions earlier than Excel 2007, the maximum number of additional arguments that can be passed is 29, which is 30 including  _pxFnRef_. Starting in Excel 2007, this limit is raised to 254, which is 255 including  _pxFnRef_.
  
## Return value

Returns whatever value the user-defined function returned.
  
## Example

The following example runs **TestMacro** on sheet Macro1 in BOOK1.XLS. Make sure that the macro is on a sheet named Macro1. 
  
`\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI xlUDFExample(void)
{       
   XLOPER12 xMacroName, xMacroRef, xRes;
   xMacroName.xltype = xltypeStr;
   xMacroName.val.str = L"\044[BOOK1.XLSX]Macro1!TestMacro";
   Excel12(xlfEvaluate, &xMacroRef, 1, (LPXLOPER12)&xMacroName);
   Excel12(xlUDF, &xRes, 1, (LPXLOPER12)&xMacroRef);
   return 1;
}
```

## See also

- [C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

