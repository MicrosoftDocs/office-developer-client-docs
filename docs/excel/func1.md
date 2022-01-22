---
title: "Func1"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Func1
keywords:
- func1 function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 801b14ef-0be8-4b97-919d-a9d413705d1c
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Func1

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Example user-defined worksheet function demonstrates the return of a static string value. When GENERIC.xll is loaded, it registers this function so that it can be called from the worksheet.
  
```cs
LPXLOPER12 WINAPI Func1(LPXLOPER12 px);
```

## Parameters

 _px_ (**LPXLOPER**)
  
This argument is ignored, and serves only to trigger Microsoft Excel to call the function.
  
## Property value/Return value

 **LPXLOPER12**: Always the string "Func1"
  
### Example

See `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also



[Functions in the Generic DLL](functions-in-the-generic-dll.md)

