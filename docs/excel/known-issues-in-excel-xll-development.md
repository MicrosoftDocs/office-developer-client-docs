---
title: "Known Issues in Excel XLL Development"
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- known issues [excel 2007] 
ms.localizationpriority: medium
ms.assetid: 3dfecc0b-a91c-448e-8721-5d3486b625fa

---

# Known Issues in Excel XLL Development

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
This topic describes known issues in Microsoft Excel that you might encounter in XLL development.
  
## Unregistering XLL Commands and Functions

When an XLL registers a function or command, Excel creates a new name for the resource and associates a reference to the DLL function with that name. The name is taken from the fourth argument, *pxFunctionText*, of the [xlfRegister](xlfregister-form-1.md) function. This name is hidden from the normal dialog boxes for managing worksheet names. To unregister a function or command, you must delete the name by using the [xlfSetName](xlfsetname.md) function, passing the name but not passing a definition. However, a bug prevents this from removing the name from the Function Wizard lists.
  
## Argument Description String Truncation in the Function Wizard

The *pxArgumentHelp1*  parameter and all subsequent parameters of the **xlfRegister** function are optional strings that correspond to the arguments of the XLL function. The Function Wizard displays these to provide help in the argument construction dialog box. Sometimes Excel truncates the string that corresponds to the final argument by one or two characters when displaying it in the dialog box. You can avoid this by adding an additional "empty string" as the last "argument help" parameter of your function registration.
  
## Binary Name Scope Limitation

Binary names and their data can be retrieved only when the worksheet that was active at the time they were created is again active. Because worksheet functions cannot activate worksheets within a workbook (only commands can do this), applications of binary names are very limited. If you have a command that is only invoked from a particular worksheet, for example, you could use a binary name to store command-related data.
  
## xlSet and Workbooks with Array Formulas

In Excel 2003 and earlier versions, the [xlSet function](xlset.md) fails if you try to assign values to a range on a worksheet that is not the active worksheet, where the equivalent range on the active sheet contains an array formula. In this case, Excel displays the message "You cannot change part of an array." This was fixed in Excel 2007.
  
## Circular References are Tolerated in Data Tables

Excel currently does not raise an error if the calculation that a data table is based on refers to something in the table itself. As unlikely as this scenario might be, you should be careful when you are creating or modifying formulas that are used to calculate data table values.
  
## Converting an Integer XLOPER12 to an XLOPER

Because the integer type **xltypeInt** is a 32-bit signed integer in the **XLOPER12** data type, but it is only a 16-bit signed integer in the **XLOPER** data type, it is possible that some integer **XLOPER12** values cannot be contained in an integer **XLOPER**. Where Excel converts this type internally, it gets around this problem by converting the type to a floating-point **xltypeNum** **XLOPER**.
  
The Framework [XLOper12ToXLOper](xloper12toxloper.md) function mirrors this behavior to be consistent with Excel internally. When you call this function, you should not assume that the returned **XLOPER** will always be **xltypeInt**; reading **my_xloper.val.w** gives a false value if the **my_xloper** type is **xltypeNum**.
  
## Returning XLOPER or XLOPER12 by Modifying Arguments in Place

Excel permits the registration of functions that return an **XLOPER** or **XLOPER12** by modifying an argument in place. However, if an **XLOPER**/ **XLOPER12** argument points to memory, and the pointer is then overwritten by the return value of the DLL function, Excel can leak memory. Excel does not display an error, but it might eventually crash. Also, if the DLL allocated memory for the return value, Excel might try to free that memory, which could cause an immediate application crash. Therefore, you should not modify **XLOPER**/ **XLOPER12** arguments in place. All **XLOPER** or **XLOPER12** arguments should be treated as strictly read-only.
  
For more information, see [Memory Management in Excel](memory-management-in-excel.md).
  
## See also

[XLOper12ToXLOper](xloper12toxloper.md)
[Developing Excel XLLs](developing-excel-xlls.md)  
[Excel XLL SDK API Function Reference](excel-xll-sdk-api-function-reference.md)  
[Memory Management in Excel](memory-management-in-excel.md)