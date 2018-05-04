---
title: "Displaying Dialog Boxes from Within a DLL or XLL"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- xlls [excel 2007], displaying dialog boxes from,dialog boxes [Excel 2007], displaying from a DLL or XLL,DLLs [Excel 2007], displaying dialog boxes from
 
localization_priority: Normal
ms.assetid: e77ac555-331d-41c8-a000-7b178959754d
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Displaying Dialog Boxes from Within a DLL or XLL

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
To display a Win32 dialog box using, for example, the Windows SDK function **DialogBox**, you must first obtain the full 32-bit instance and main window handles for Excel. For more information, see [How to: Access Excel Instance and Main Window Handles](how-to-access-excel-instance-and-main-window-handles.md). 
  
Assuming your project contains the dialog box resource, you must take several steps to set the message-handling routine to that of the newly displayed dialog box and to restore the Excel message handling routine when the dialog box is closed. The example command [fShowDialog](fshowdialog.md) in the Generic project demonstrates the use of the Windows functions to do this correctly. 
  
You can also display dialog boxes using the C API without having to use Windows SDK functions. However, the dialog box capabilities of the C API are very limited compared with those of Windows, Visual Basic for Applications (VBA), or the Microsoft Foundation Classes (MFC). (For example, C API dialog boxes are always modal).
  
## See also

#### Concepts

[Creating XLLs](creating-xlls.md)
  
[Developing DLLs](developing-dlls.md)
  
[How to: Access Excel Instance and Main Window Handles](how-to-access-excel-instance-and-main-window-handles.md)
  
[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

