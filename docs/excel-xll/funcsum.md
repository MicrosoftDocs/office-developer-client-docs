---
title: "FuncSum"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- FuncSum
keywords:
- funcsum function [excel 2007]
 
localization_priority: Normal
ms.assetid: 934192ef-8a89-4dbb-bd37-01e92ba24256
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# FuncSum

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Example user-defined worksheet function that takes 1 to 29 arguments and computes their sum. Each argument can be a single number, a range, or an array. When GENERIC.xll is loaded, it registers this function so that it can be called from the worksheet. 
  
```cs
LPXLOPER12 WINAPI FuncSum(LPXLOPER12 px1, LPXLOPER12 px2, LPXLOPER12 px3,LPXLOPER12 px4, LPXLOPER12 px5, LPXLOPER12 px6, LPXLOPER12 px7,LPXLOPER12 px8, LPXLOPER12 px9, LPXLOPER12 px10, LPXLOPER12 px11,LPXLOPER12 px12, LPXLOPER12 px13, LPXLOPER12 px14, LPXLOPER12 px15,LPXLOPER12 px16, LPXLOPER12 px17, LPXLOPER12 px18, LPXLOPER12 px19,LPXLOPER12 px20, LPXLOPER12 px21, LPXLOPER12 px22, LPXLOPER12 px23,LPXLOPER12 px24, LPXLOPER12 px25, LPXLOPER12 px26, LPXLOPER12 px27,LPXLOPER12 px28, LPXLOPER12 px29);
```

## Parameters

 _px1-px29_ (**LPXLOPER12**)
  
Pointers to **XLOPER12** arguments. The function accepts any kind of input type but is coded only to operate on numbers, literal arrays of numbers, and ranges containing only numbers or blank cells. If fewer than 29 arguments are supplied, the remaining arguments are supplied as **xltypeMissing**.
  
## Property value/Return value

(**LPXLOPER12 xltypeNum** or **xltypeErr**)
  
The sum of the arguments or #VALUE! if there are non-numerics in the supplied argument list or in a cell in a range or element in an array.
  
### Example

See  `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also



[Functions in the Generic DLL](functions-in-the-generic-dll.md)

