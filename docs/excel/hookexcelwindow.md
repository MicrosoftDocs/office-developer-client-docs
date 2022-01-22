---
title: "HookExcelWindow"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- HookExcelWindow
keywords:
- hookexcelwindow function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 13f0ae5e-9951-4e89-a245-7cf68c6f6724
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# HookExcelWindow

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Installs **ExcelCursorProc** so that it is called before the Microsoft Excel main **WndProc**.
  
```cs
extern void FAR PASCAL HookExcelWindow(HANDLE hWndExcel);
```

## Parameters

 _hWndExcel_ (**HANDLE**)
  
The Excel main Windows handle.
  
## Property value/Return value

The function does not return a value.
  
## Remarks

The function obtains the address of the Excel **WndProc** through the use of **GetWindowLong()**. It stores this value in a global that can be used to call the default **WndProc** and also to restore it. Finally, it replaces this address with the address of **ExcelCursorProc** using **SetWindowLong()**.
  
### Example

See `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also



[Functions in the Generic DLL](functions-in-the-generic-dll.md)

