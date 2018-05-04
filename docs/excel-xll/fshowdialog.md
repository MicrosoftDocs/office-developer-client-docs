---
title: "fShowDialog"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- fShowDialog
keywords:
- fshowdialog function [excel 2007]
 
localization_priority: Normal
ms.assetid: 6cc01075-7221-488e-870f-433da62930e6
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# fShowDialog

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Example user-defined command that loads and displays an example native Windows dialog box. When GENERIC.xll is loaded, it creates a user-defined menu, Generic, through which this command is accessed.
  
```cs
int WINAPI fShowDialog(void);
```

## Parameters

The function takes no parameters.
  
## Property Value/Return Value

The function return integer zero to indicate successful completion
  
## Remarks

The steps to display the native Windows dialog box are as follows:
  
1. Obtain the Microsoft Excel main Windows handle using **GetHwnd**.
    
2. Hook the Excel main window using **HookExcelWindow**.
    
3. Display the dialog box using **DialogBox**.
    
4. Unhook the Excel main window using **UnhookExcelWindow**.
    
### Example

See  `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also

#### Concepts

[Functions in the Generic DLL](functions-in-the-generic-dll.md)

