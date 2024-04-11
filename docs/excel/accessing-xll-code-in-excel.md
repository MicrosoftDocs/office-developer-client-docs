---
title: "Accessing XLL code in Excel"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- accessing xll code [excel 2007],XLLs [Excel 2007], accessing code,commands [Excel 2007], registration,functions [Excel 2007], registration,calling XLLs from Excel,registering commands [Excel 2007],registering functions [Excel 2007] 
ms.assetid: 6e4bf1f3-8eca-4be5-9632-75355ac31d61

ms.localizationpriority: high
---

# Accessing XLL code in Excel

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
To be accessible in Microsoft Excel, the functions and commands that an XLL contains:
  
- Must be exported by the XLL.
    
- Must be registered with Excel.
    
## Registering functions and commands with Excel

Registration tells Excel the following about a DLL entry point:
  
- Whether it is hidden or, if a function, whether it is visible in the Function Wizard.
    
- Whether it is callable only from an XLM macro sheet, or also from a worksheet.
    
- If a command, whether it is a worksheet function or a macro sheet equivalent function.
    
- What its XLL/DLL export name is, and what name you want Excel to use.
    
- If it is a function:
    
  - What data types it returns and takes as arguments.
    
  - Whether it returns its result by modifying an argument in place.
    
  - Whether it is volatile.
    
  - Whether it is thread safe (supported starting in Excel 2007).
    
  - What text the Paste Function Wizard and AutoComplete editor should display to help with calling the function.
    
  - Which function category it should be listed under.
    
This is all achieved using the C API function [xlfRegister](xlfregister-form-1.md), equivalent to the XLM function **REGISTER**.
  
## Calling XLL functions directly from Excel

Once they are registered, XLL worksheet and macro sheet functions can be called from anywhere a built-in function can be called from:
  
- A single-cell or array formula on a worksheet.
    
- A single-cell or array formula on a macro sheet.
    
- The definition of a defined name.
    
- The condition and limit fields in a conditional format dialog box.
    
- From another add-in via the C API function [xlUDF](xludf.md).
    
- From Visual Basic for Applications (VBA) via the **Application.Run** method. 
    
You can obtain a reference to the calling cell or range of cells within your function using the C API function **xlfCaller**. If the function was called from the cell's conditional format expression, you are still returned a reference to the associated cell or cells, so you cannot assume that the cell's formula contains the XLL function. If your function was called from a VBA user-defined function (UDF), **xlfCaller** again returns the address of the cells that called the VBA function. For more information, see [xlfCaller](xlfcaller.md).
  
> [!NOTE]
> Excel also calls XLL function code from the **Paste Function Wizard** and **Replace** dialog boxes. You might need to restrict your code's normal running in the case of the **Paste Function Arguments** dialog box, especially where your function can take a long time to execute. To detect if your function is being called from either of these dialog boxes, you must implement some code in your project that iterates through all the open windows to determine if the front window is one of these dialog boxes, and, if so, which one. 
  
## Calling XLL commands directly from Excel

Once they are registered, XLL commands can be called in all the ways that other user-defined macros can be called:
  
- By being associated with a control object embedded on a worksheet.
    
- From the Run Macro dialog box.
    
- From a VBA user-defined macro using the **Application.Run** method. 
    
- From a customized menu item or toolbar.
    
- Using a shortcut keystroke set up when registering the command.
    
- As the command to be run when a specified event is trapped.
    
> [!NOTE]
> XLL commands are hidden in that they do not appear on the list of available macros in Excel dialog boxes. But they can be entered manually into the macro name field. Excel expects the registered-as name in these dialog boxes, not the DLL export name. 
  
All XLL commands registered with Excel are assumed by Excel to be of the following form:
  
```cs
short WINAPI xll_cmd_name(void)
{
// Function code...
    return 1;
}

```

Excel ignores the return value unless it is called from an XLM macro sheet, in which case the return value is converted to **TRUE** or **FALSE**. You should therefore return 1 if your command executed successfully, and 0 if it failed or was canceled by the user.
  
You can obtain information about how your command was invoked using the C API function **xlfCaller**. For more information, see [xlfCaller](xlfcaller.md).
  
Starting in Excel 2007 user interface is very different from earlier versions. The C API functions that permit the addition and deletion of custom menu bars, menus, submenus, menu items, custom toolbars and toolbar buttons are still supported in most cases. However, they may not always make the added item available in a way that your users are familiar with. You should carefully check that any added functionality is still accessible, or implement a version-specific customization. Starting in Excel 2007 the user interface is best customized by using a managed code module that can then be tightly coupled to your XLL commands.
  
## See also

- [Creating XLLs](creating-xlls.md)
- [Call XLL Functions from the Function Wizard or Replace Dialog Boxes](how-to-call-xll-functions-from-the-function-wizard-or-replace-dialog-boxes.md)
- [Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md)
- [Developing Excel XLLs](developing-excel-xlls.md)



