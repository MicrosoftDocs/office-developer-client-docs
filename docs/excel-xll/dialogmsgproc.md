---
title: "DIALOGMsgProc"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- DIALOGMsgProc
keywords:
- dialogmsgproc function [excel 2007]
 
localization_priority: Normal
ms.assetid: 9a538e83-ba34-4806-bb8c-7cda3beb6b66
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# DIALOGMsgProc

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
This procedure is associated with the native Windows dialog box that [fShowDialog](fshowdialog.md) displays. It provides the service routines called by Windows for the events (messages) that occur when the user operates one of the dialog box's buttons, entry fields, or controls. 
  
```cs
BOOL CALLBACK DIALOGMsgProc(HWND hWndDlg, UINT message, WPARAM wParam, LPARAM lParam);
```

## Parameters

 _hWndDlg_ ( **HWND**)
  
Contains the HWND Windows handle of the dialog box.
  
 _message_ ( **UINT**)
  
The message to respond to.
  
 _wParam_ ( **WPARAM**)
  
 _lParam_ ( **LPARAM**)
  
Arguments passed by Windows.
  
## Property Value/Return Value

 **TRUE** if message processed, **FALSE** if not. 
  
### Example

See  `\SAMPLES\GENERIC\GENERIC.C` for the source code for this function. 
  
## See also

#### Concepts

[Functions in the Generic DLL](functions-in-the-generic-dll.md)

