---
title: "fExit"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- fExit
keywords:
- fexit function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: d85685fa-df70-45bb-b629-a9d43b5cb926
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# fExit

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Example user-defined command that unloads GENERIC.xll. When GENERIC.xll is loaded, it creates a user-defined menu, Generic, through which this command is accessed. 
  
```cs
int WINAPI fExit(void);
```

## Parameters

The function takes no parameters.
  
## Property value/Return value

The function always returns 1.
  
## Remarks

This is a user-initiated routine to exit GENERIC.xll You should avoid simply calling  `UNREGISTER("GENERIC.XLL")` in this function. This would forcefully unregister all the functions in this DLL, even if they are registered somewhere else. Instead, unregister the functions one at a time. 
  
### Example

See  `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also



[Functions in the Generic DLL](functions-in-the-generic-dll.md)

