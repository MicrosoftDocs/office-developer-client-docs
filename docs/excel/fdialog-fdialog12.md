---
title: "fDialog/fDialog12" 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- fDialog
- fDialog12
keywords:
- fdialog function [excel 2007],fDialog12 function [Excel 2007] 
ms.localizationpriority: medium
ms.assetid: a9a47408-07d1-4a00-9596-abc48b12392f
<<<<<<< HEAD

=======
>>>>>>> c31298c4512c31c77f2d7875cd3894cb29c028f6
---

# fDialog/fDialog12

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Example user-defined command that demonstrates how to create a Microsoft Excel UDD (user-defined dialog box) within a DLL by using the dialog box capabilities in the C API. When GENERIC.xll is loaded, it creates a user-defined menu, Generic, through which this command is accessed.
  
```cs
int WINAPI fDialog(void);
```

## Parameters

The function takes no parameters.
  
## Property value/Return value

The function always returns 1.
  
### Example

See `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also

[Functions in the Generic DLL](functions-in-the-generic-dll.md)
