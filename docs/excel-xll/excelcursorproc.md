---
title: "ExcelCursorProc"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- ExcelCursorProc
keywords:
- excelcursorproc function [excel 2007]
 
localization_priority: Normal
ms.assetid: 43759617-998d-4030-a17d-c4bbe35ffaf9
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# ExcelCursorProc

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
When a modal dialog box is displayed over the Microsoft Excel window, the cursor is a busy cursor over the Excel window. This **WndProc** traps WM_SETCURSOR type Windows messages and changes the cursor back to a normal arrow. 
  
```cs
LRESULT CALLBACK ExcelCursorProc(HWND hwnd, UINT wMsg, WPARAM wParam, LPARAM lParam);
```

## Parameters

 _hWndDlg_ (**HWND**)
  
Contains the HWND Windows handle of the dialog box.
  
 _message_ (**UINT**)
  
The message to respond to.
  
 _wParam_ (**WPARAM**)
  
 _lParam_ (**LPARAM**)
  
Arguments passed by Windows.
  
## Property value/Return value

LRESULT: 0 if the message was handled, otherwise the result returned by the default **WndProc**.
  
### Example

See  `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also



[Functions in the Generic DLL](functions-in-the-generic-dll.md)

