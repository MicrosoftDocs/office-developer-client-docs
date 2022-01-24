---
title: "Creating XLLs"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
keywords:
- dlls [excel 2007], calling into excel,xlAutoFree function [Excel 2007],xlAutoFree12 function [Excel 2007],xlcall32.lib [Excel 2007],xlAutoRegister function [Excel 2007],xlcall.cpp [Excel 2007],xlAutoRemove function [Excel 2007],xlAddInManagerInfo function [Excel 2007],xlAutoAdd function [Excel 2007],xlAutoOpen function [Excel 2007],xlAutoClose function [Excel 2007],DLLs [Excel 2007], turning into XLLs,XLLs [Excel 2007], calling into Excel,xlAutoRegister12 function [Excel 2007],xlcall.h [Excel 2007],xlAddInManagerInfo12 function [Excel 2007]
 
ms.assetid: 7754998f-4e13-4a37-9724-43b6ee6c919b

ms.localizationpriority: high
---

# Creating XLLs

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
If your DLL is self-contained or relies only on other libraries, you must know how to enable Microsoft Excel to access its functions and commands. For more information, see [Access DLLs in Excel](how-to-access-dlls-in-excel.md). 
  
However, if your DLL needs to access Excel functionality (for example, to get the contents of a cell, to call a worksheet function, or to interrogate Excel to obtain workspace information), your code must be able to call back into Excel.
  
The Excel C API provides several functions that enable DLLs to call back into Excel. To access these, the DLL must be linked statically at compile time with the Excel 32-bit library, xlcall32.lib. The static library is downloadable from Microsoft as part of the Microsoft Excel 2013 XLL SDK, which includes both 32-bit and 64-bit versions of this library.
  
## Enabling DLLs to Call Back into Excel

For a DLL to be able to access the functionality in Excel and get or set workspace information, it must first obtain the addresses of the Excel callback functions **Excel4**, **Excel4v**, **Excel12**, and **Excel12v**. The last two were introduced in Excel 2007 and are available in subsequent versions. To access all of these, the DLL project must include references to the following files from the Excel 2013 XLL SDK. If you want to access only the first two callbacks (in any version of Excel), your project needs to include only the first two files.
  
### Xlcall.h

The Xlcall.h file contains the following items:
  
- Function prototypes for all callback functions.
    
- Definitions of the data structures that the callbacks use to exchange data between the DLL/XLL and Excel, and data-type constant definitions.
    
- Definitions of the C API function and command equivalents of the worksheet, macro sheet functions, and supported Excel commands.
    
- Definitions of callback function return values.
    
You should use the **#include** directive for this file, directly or indirectly via another header file, in all files that access the C API or that handle data types that the C API uses. 
  
### Xlcall32.lib

The Xlcall32.lib library exports the first two callbacks, **Excel4** and **Excel4v**, and also the **XlCallVer** function. Without a reference to this library in your project, the linker cannot create the XLL if you have used any of these callbacks in your code. (You can obtain the addresses of these functions by linking dynamically to the equivalent Xlcall32.dll that is copied to your system as part of a normal Excel installation.) 
  
### Xlcall.cpp

The Excel callbacks **Excel12** and **Excel12v** are not exported in Xlcall32.lib. This ensures that XLL projects that you create starting in Excel 2007 will also work with earlier versions of Excel. The Xlcall.cpp module contains code for the **Excel12** and **Excel12v** functions, which call into an Excel entry point starting in Excel 2007, or return a safe error value if you are running an earlier version of Excel. You should include this module in your project if you want to create an XLL that runs starting in Excel 2007 and that is able to use the new data types that handle larger grids and longer Unicode strings. 
  
> [!NOTE]
> Starting with the Excel 2010 SDK, this file can be compiled for both 32-bit and 64-bit XLLs. 
  
## Turning DLLs into XLLs: Add-in Manager Interface Functions

An XLL is a DLL that exports several procedures that are called by Excel or the Excel Add-in Manager. These procedures are described briefly here and discussed in detail in [Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md). All of these DLL callbacks start with the prefix **xlAuto**. Only one of these, the command **xlAutoOpen**, is required. It is called when the add-in is activated, and it is typically used to register XLL functions and commands with Excel and to do other initialization tasks. The function signatures and example implementations of all of the **xlAuto** functions are provided in later sections. 
  
Even though **xlAutoOpen** is the only required one of these callbacks, your add-in may also need to export others depending on its behavior. 
  
Excel 2007 introduced a new data type, **XLOPER12**, to accommodate larger grids and to support long Unicode strings. **XLOPER12** is described later in this topic. Whereas **xlAuto** functions take or return the old data type **XLOPER**, new versions of these functions were introduced in Excel 2007 that use **XLOPER12** data types. With the exception of **xlAutoFree12**, which you must sometimes implement to avoid **XLOPER12** memory leaks, you can safely omit all the version 12 **xlAuto** functions, in which case, starting in Excel 2007, Excel calls the **XLOPER** versions. 
  
### xlAutoOpen

Excel calls the [xlAutoOpen](xlautoopen.md) function whenever the XLL is activated. The add-in will be activated at the start of an Excel session if it was active in the last Excel session that ended normally. The add-in is activated if it is loaded during an Excel session. The add-in can be deactivated and reactivated during an Excel session, and the function is called on reactivation. 
  
You should use **xlAutoOpen** to register XLL functions and commands, initialize data structures, customize the user interface, and so on. 
  
If your add-in implements and exports the [xlAutoRegister](xlautoregister-xlautoregister12.md) function or the [xlAutoRegister12](xlautoregister-xlautoregister12.md) function, Excel might attempt to activate and register a function or command without first calling the **xlAutoOpen** function. In this case, you should ensure that your add-in is sufficiently initialized for your function or command to work properly. If it is not, you should either fail the attempt to register the function or command, or carry out the necessary initialization. 
  
### xlAutoClose

Excel calls the [xlAutoClose](xlautoclose.md) function whenever the XLL is deactivated. The add-in will be deactivated when an Excel session ends normally. If the user deactivates the add-in during an Excel session, the function is called. 
  
You should use **xlAutoClose** to unregister functions and commands, release resources, undo customizations, and so on. 
  
> [!NOTE]
> There is a known issue with the unregistration of functions and commands. For more information, see [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md). 
  
### xlAutoAdd

Excel calls the [xlAutoAdd function](xlautoadd.md) whenever the user activates the XLL during an Excel session by using the Add-In Manager. This function is not called when Excel starts and loads a preinstalled add-in. 
  
You can use this function to display a custom dialog box that tells the user that the add-in has been activated, to read from or write to the registry, or to check licensing information.
  
### xlAutoRemove

Excel calls the [xlAutoRemove](xlautoremove.md) function whenever the user deactivates the XLL during an Excel session by using the Add-In Manager. This function is not called when an Excel session closes, normally or abnormally, with the add-in installed. 
  
You can use this function to display a custom dialog box that tells the user that the add-in has been deactivated, or to read from or write to the registry.
  
### xlAddInManagerInfo/xlAddInManagerInfo12

Excel calls the [xlAddInManagerInfo](xladdinmanagerinfo-xladdinmanagerinfo12.md) function when the Add-in Manager is invoked for the first time in an Excel session. If Excel passes an argument equal to 1, this function should return a string (typically, the name of the add-in); otherwise, it should return **#VALUE!**.
  
Starting in Excel 2007, Excel calls the **xlAddInManagerInfo12** function in preference to the **xlAddInManagerInfo** function if it is exported by the XLL. The **xlAddInManagerInfo12** function should work in the same way as the **xlAddInManagerInfo** function to avoid version-specific differences in the behavior of the XLL. The **xlAddInManagerInfo12** function should return an **XLOPER12** data type, whereas the **xlAddInManagerInfo** function should return an **XLOPER** data type. 
  
### xlAutoRegister/xlAutoRegister12

Excel calls the [xlAutoRegister](xlautoregister-xlautoregister12.md) function whenever a call has been made to the XLM function **REGISTER**, or the C API equivalent [xlfRegister](xlfregister-form-1.md) function, with the return and argument types missing for the function being registered. The **xlAutoRegister** function allows the XLL to search its internal lists of exported functions and commands to register the function with the argument and return the specified types. 
  
Starting in Excel 2007, Excel calls the **xlAddInRegister12** function in preference to the **xlAddInRegister** function if it is exported by the XLL. 
  
> [!NOTE]
> If **xlAddInRegister**/ **xlAddInRegister12** tries to register the function without supplying the argument and return types, a recursive calling loop occurs that eventually overflows the call stack and causes Excel to close or stop responding. 
  
### xlAutoFree/xlAutoFree12

Excel calls the [xlAutoFree/xlAutoFree12](xlautofree-xlautofree12.md) function just after an XLL worksheet function returns an **XLOPER**/ **XLOPER12** data type with a flag set that tells Excel there is memory that the XLL still needs to release. This enables the XLL to return dynamically allocated arrays, strings, and external references to the worksheet without memory leaks. Starting in Excel 2007, the **XLOPER12** data type is supported. For more information, see [Memory Management in Excel](memory-management-in-excel.md).
  
> [!NOTE]
> Starting in Excel 2007, when Excel is configured to use multithreaded worksheet recalculation, the **xlAutoFree**/ **xlAutoFree12** function is called on the same thread that was just used to call the function that returned it. The call to **xlAutoFree**/ **xlAutoFree12** is always made before any subsequent worksheet cells are evaluated on that thread. This simplifies thread-safe design in your XLL. For more information, see [Multithreaded Recalculation in Excel](multithreaded-recalculation-in-excel.md). 
  
### Creating 64-bit XLLs

Excel and user-defined functions can run on 64-bit operating systems to take advantage of performance benefits over 32-bit operating systems. Excel passes values in **XLOPER12** structures that include information about the types for the data. Be careful when you convert between values in the **XLOPER12** structure and native types like **int** or pointers to preserve the values in the larger type. 
  
## See also



[Call XLL Functions from the Function Wizard or Replace Dialog Boxes](how-to-call-xll-functions-from-the-function-wizard-or-replace-dialog-boxes.md)
  
[Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md)
  
[Developing Excel XLLs](developing-excel-xlls.md)

