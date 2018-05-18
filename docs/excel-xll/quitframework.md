---
title: "QuitFramework"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- QuitFramework
keywords:
- quitframework function
 
localization_priority: Normal
ms.assetid: d17a3efe-c278-4ef1-b8f9-b958ae012361
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# QuitFramework

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework library function that uninitializes the Framework library, which simply re-initializes the temporary **XLOPER**/ **XLOPER12** memory data structures, freeing any memory that has already been allocated. 
  
```cs
short WINAPI QuitFramework(void);
```

## Parameters

This function takes no arguments.
  
## Property Value/Return Value

This function does not return a value.
  
## See also



[Functions in the Framework Library](functions-in-the-framework-library.md)

