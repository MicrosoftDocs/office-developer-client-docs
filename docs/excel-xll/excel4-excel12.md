---
title: "Excel4/Excel12"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Excel12
- Excel4
keywords:
- excel4 function [excel 2007],Excel12 function [Excel 2007]
 
localization_priority: Normal
ms.assetid: 2404f10d-8641-4ee6-a909-1c5a26610f80
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Excel4/Excel12

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Calls an internal Microsoft Excel worksheet function, macro sheet function or command, or XLL-only special function or command, from within a DLL/XLL or code resource.
  
All recent versions of Excel support **Excel4**. Starting in Excel 2007, **Excel12** is supported. 
  
These functions can be called only when Excel has passed control to the DLL or XLL. They can also be called when Excel has passed control indirectly via a call to Visual Basic for Applications (VBA). They cannot be called at any other time. For example, they cannot be called during calls to the [DllMain](http://msdn.microsoft.com/library/base.dllmain%28Office.15%29.aspx) function or other times when the operating system has called the DLL, or from a thread created by the DLL. 
  
The [Excel4v and Excel12v](excel4v-excel12v.md) functions accept their arguments as an array, whereas the **Excel4** and **Excel12** functions accept their arguments as a variable-length list on the stack. In all other respects, **Excel4** behaves the same as **Excel4v**, and **Excel12** behaves the same as **Excel12v**.
  
```cs
int Excel4(int iFunction, LPXLOPER pxRes, int iCount, LPXLOPER argument1, ...);
int Excel12(int iFunction, LPXLOPER12 pxRes, int iCount, LPXLOPER12 argument1, ...);
```

## Parameters

 _iFunction_ ( **int**)
  
A number that indicates the command, function, or special function you want to call. For a list of valid  _iFunction_ values, see the following Remarks section. 
  
 _pxRes_ ( **LPXLOPER** or **LPXLOPER12**)
  
A pointer to an **XLOPER** (with **Excel4**) or an **XLOPER12** (with **Excel12**) that will hold the result of the evaluated function.
  
 _iCount_ ( **int**)
  
The number of subsequent arguments that will be passed to the function. In versions of Excel up to 2003, this can be any number from 0 through 30. Starting in Excel 2007, this can be any number from 0 through 255.
  
 _argument1, ..._ ( **LPXLOPER** or **LPXLOPER12**)
  
The optional arguments to the function. All arguments must be pointers to **XLOPER** or **XLOPER12** values. 
  
## Return Value

Returns one of the following integer ( **int**) values.
  
|**Value**|**Return code**|**Description**|
|:-----|:-----|:-----|
|0  <br/> |**xlretSuccess** <br/> |The function was called successfully. This does not mean that the function did not return an Excel error value; to find that out, you must look at the type and value of the resulting  _pxRes_ parameter.  <br/> |
|1  <br/> |**xlretAbort** <br/> |The command or function was terminated abnormally (internal abort). This can occur if an XLM macro sheet closes itself by calling **CLOSE**, or if Excel is out of memory. If Excel returns this error, the calling function must exit immediately. The DLL is permitted to call **xlFree** only before exiting. All other calls to the C API are not permitted. The user can save any work interactively by using the **Save** command on the **File** menu.  <br/> |
|2  <br/> |**xlretInvXlfn** <br/> |An invalid function number was supplied. If you are using constants from the Xlcall.h header file, this should not occur unless you are calling something that is not supported in the version of Excel you are running.  <br/> |
|4  <br/> |**xlretInvCount** <br/> |An invalid number of arguments was entered. In versions up to Excel 2003, the maximum number of arguments any function can take is 30. Starting in Excel 2007, the maximum number is 255. Some require a fixed or minimum number of arguments.  <br/> |
|8  <br/> |**xlretInvXloper** <br/> |An invalid **XLOPER** or **XLOPER12** was passed to the function, or an argument of the wrong type was used.  <br/> |
|16  <br/> |**xlretStackOvfl** <br/> |A stack overflow occurred. Use **xlStack** to monitor the amount of room left on the stack. Avoid allocating very large local (automatic) arrays and structures on the stack where possible; make them static. (Note that a stack overflow might occur without being detected.)  <br/> |
|32  <br/> |**xlretFailed** <br/> |A command-equivalent function failed. This is equivalent to a macro command displaying the macro error alert dialog box.  <br/> |
|64  <br/> |**xlretUncalced** <br/> |An attempt was made to dereference a cell that has not been calculated yet, because it is scheduled to be recalculated after the current cell. In this case, the DLL should return control to Excel immediately. The DLL is permitted to call **xlFree** only before exiting. All other calls to the C API are not permitted. For more information about which functions can and cannot access the values of cells that have not been recalculated, see [Excel Commands, Functions, and States](excel-commands-functions-and-states.md).  <br/> |
|128  <br/> |**xlretNotThreadSafe** <br/> |An attempt was made to call a function that is not, or might not be, thread safe during a multithreaded recalculation of the workbook.  <br/> Starting in Excel 2007, this value is returned, and only within XLL worksheet functions declared as thread safe.  <br/> |
|256  <br/> |**xlRetInvAsynchronousContext** <br/> |The asynchronous function handle is invalid.  <br/> This value is used only by Excel 2010.  <br/> |
|512  <br/> |**xlRetNotClusterSafe** <br/> |The call is not supported on clusters.  <br/> This value is used only by Excel 2010.  <br/> |
   
## Remarks

### Valid iFunction values

Valid **iFunction** values are any of the **xlf...** or **xlc...** constants defined in the Xlcall.h header file or any of the following special functions. 
  
|||||
|:-----|:-----|:-----|:-----|
|**xlAbort** <br/> |**xlEnableXLMsgs** <br/> |**xlGetInst** <br/> |**xlSheetNm** <br/> |
|**xlCoerce** <br/> |**xlFree** <br/> |**xlGetName** <br/> |**xlStack** <br/> |
|**xlDefineBinaryName** <br/> |**xlGetBinaryName** <br/> |**xlSet** <br/> |**xlUDF** <br/> |
|**xlDisableXLMsgs** <br/> |**xlGetHwnd** <br/> |**xlSheetId** <br/> ||
   
### Different Types of Functions

 **Excel4** and **Excel12** distinguish among three classes of functions. The functions are classified according to the three states in which Excel might call the DLL. 
  
- Class 1 applies when the DLL is called from a worksheet as a result of recalculation. 
    
- Class 2 applies when the DLL is called from within a function macro or from a worksheet where it was registered with a number sign (#) in the type text.
    
- Class 3 applies when a DLL is called from an object, macro, menu, toolbar, shortcut key, **ExecuteExcel4Macro** method, or the **Tools/Macro/Run** command. For more information, see [Excel Commands, Functions, and States](excel-commands-functions-and-states.md).
    
The following table shows what functions are valid in each class.
  
|**Class 1**|**Class 2**|**Class 3**|
|:-----|:-----|:-----|
|Any worksheet function  <br/> Any XLL-only **xl...** function except **xlSet**.  <br/> **xlfCaller** <br/> |Any worksheet function  <br/> Any **xl...** function except **xlSet**.  <br/> Macro sheet functions, including **xlfCaller**, that return a value but perform no action that affects the workspace or any open workbook.  <br/> |Any function, including **xlSet** and command-equivalent functions.  <br/> |
   
### Displaying the Dialog Box for a Command-Equivalent Function

If a command-equivalent function has an associated dialog box, you can set the **xlPrompt** bit in **iFunction**. This means that Excel displays the appropriate dialog box before carrying out the command.
  
### Writing International DLLs

If you set the **xlIntl** bit in **iFunction**, the function or command is carried out as if it were being called from an International Macro Sheet. This means that the command behaves as it would on the U.S. version of Excel, even if it is running on an international (localized) version.
  
### xlretUncalced or xlretAbort

After receiving one of these return values, your DLL must clean up and return control to Excel immediately. Callbacks into Excel via the C API, except **xlFree**, are disabled after receiving one of these return values.
  
## Example

The following example uses the **Excel12** function to select the cell from which it was called. 
  
This code example is part of a larger example provided in the Excel 2010 XLL SDK, at the following location where you installed the SDK:
  
\Samples\Example\Example.c.
  
> [!NOTE]
> This function calls a command macro (xlcSelect) and, therefore, works only if it is called from an XLM macro sheet. 
  
```cs
short WINAPI Excel12Example(void)
{
    XLOPER12 xRes;
    Excel12(xlfCaller, &xRes, 0);
    Excel12(xlcSelect, 0, 1, (LPXLOPER12)&xRes);
    Excel12(xlFree, 0, 1, (LPXLOPER12)&xRes);
    return 1;
}
```

## See also



[Excel4v/Excel12v](excel4v-excel12v.md)

