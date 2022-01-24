---
title: "FuncFib"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- FuncFib
keywords:
- funcfib function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 6a719f04-b2d1-4f87-a227-be561cbd3e49

---

# FuncFib

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Example user-defined worksheet function that computes the Nth Fibonacci number. When GENERIC.xll is loaded, it registers this function so that it can be called from the worksheet.
  
```cs
LPXLOPER12 WINAPI FuncFib (LPXLOPER12 pxN);
```

## Parameters

 _pxN_ (**LPXLOPER12**)
  
The value of N for which the Nth Fibonacci number is required.
  
## Property value/Return value

(**xltypeNum LPXLOPER12** if successful or **xltypeErr** otherwise) 
  
The Nth Fibonacci number.
  
## Remarks

The function uses a static variable defined within the function block as the return value **XLOPER12**. This is not thread safe, and so this function, and any worksheet function that uses this strategy for returning **XLOPER**s or **XLOPER12**s, should not be registered as thread safe starting in Excel 2007.
  
### Example

See `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also



[Functions in the Generic DLL](functions-in-the-generic-dll.md)

