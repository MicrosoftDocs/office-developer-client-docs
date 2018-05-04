---
title: "fDance"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- fDance
keywords:
- fdance function [excel 2007]
 
localization_priority: Normal
ms.assetid: 8c2f2d83-b7aa-456e-b473-a54897bc35ae
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# fDance

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Example user-defined command that changes the selected cells on the active worksheet around until the user presses **ESC**. When GENERIC.xll is loaded, it creates a user-defined menu, Generic, through which this command is accessed.
  
```cs
int WINAPI fDance(void);
```

## Parameters

The function takes no parameters.
  
## Property Value/Return Value

The function always returns 1.
  
## Remarks

This is an example of a lengthy operation. It calls the function [xlAbort](xlabort.md) occasionally. This yields the processor (helping with cooperative multitasking), and checks whether the user has pressed **ESC** to cancel the operation. If so, it offers the user a chance to cancel the abort. 
  
### Example

See  `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also

#### Concepts

[Functions in the Generic DLL](functions-in-the-generic-dll.md)

