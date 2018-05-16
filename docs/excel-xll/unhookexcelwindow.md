---
title: "UnhookExcelWindow"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- UnhookExcelWindow
keywords:
- unhookexcelwindow function
 
localization_priority: Normal
ms.assetid: 6508cb69-0c7c-4d8c-a466-dd79eb13e316
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# UnhookExcelWindow

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Removes the **ExcelCursorProc** that was previously installed by **HookExcelWindow**. This would have been done so that **ExcelCursorProc** was called before the Microsoft Excel main **WndProc**.
  
```cs
extern void FAR PASCAL UnhookExcelWindow(HANDLE hWndExcel);
```

## Parameters

 _hWndExcel_ ( **HANDLE**)
  
The Excel main Windows handle.
  
## Property Value/Return Value

The function does not return a value.
  
## Remarks

This function restores the Excel default **WndProc** using **SetWindowLong()** to restore the address that was saved by **HookExcelWindow()**.
  
### Example

See  `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also

#### Concepts

[Functions in the Generic DLL](functions-in-the-generic-dll.md)

