---
title: "Excel/Excel12f"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Excel12f
keywords:
- excel function [excel 2007],Excel12f function [Excel 2007]
 
localization_priority: Normal
ms.assetid: 4e6a9ccc-988d-42a9-8874-01f2ee29b835
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Excel/Excel12f

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework library functions. **Excel** is a wrapper for the [Excel4](excel4-excel12.md) function. **Excel12f** is a wrapper for the [Excel12](excel4-excel12.md) function. Each checks to see that none of the arguments is zero, which would indicate that the creation of a temporary **XLOPER** or **XLOPER12** failed. If an error occurs, each prints a debug message. When finished, each frees all temporary memory that might have been created for temporary **XLOPER**s and **XLOPER12**s.
  
 **Excel12f** can only be called from a DLL starting with the Excel 2007 C API library. Furthermore, it only works when running starting with Excel 2007, and fails with **xlretFailed** otherwise. 
  
```cs
int Excel(int iFunction, LPXLOPER pxRes, int iCount, 
LPXLOPER argument1, ...);
int Excel12f(int iFunction, LPXLOPER12 pxRes, int iCount, 
LPXLOPER12 argument1, ...);
```

## Parameters

 _iFunction_ ( **int**)
  
A number indicating the command or function you want to call. For more information, see [Excel4/Excel12](excel4-excel12.md).
  
 _pxRes_
  
A pointer to result of the evaluated function. Any memory pointed to in the result will have been allocated by Excel and should be freed in a call to [xlFree](xlfree.md) once it is no longer needed, or by setting **xlbitXLFree** if returning it to Excel. 
  
 _iCount_ ( **int**)
  
The number of arguments that will be passed to the function. Starting in Excel 2007, the limit is 255 arguments. In earlier versions, the limit is 30.
  
 _argument1, ..._
  
The optional arguments to the function. All arguments must be pointers to **XLOPER**s in the case of **Excel**, or **XLOPER12**s in the case of **Excel12f**.
  
## Return value

Both functions return the same error and success codes as **Excel4**, **Excel4v**, **Excel12**, and **Excel12v**. See [Excel4/Excel12](excel4-excel12.md) for a full description of these codes. In addition, these Framework functions return **xlretFailed** without calling the C API if a NULL pointer to a parameter is detected. 
  
## Example

This example passes a bad argument to the **Excel12f** function, which sends a message to the debugger. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`
  
```cs
short WINAPI Excel12fExample(void)
{
    Excel12f(xlcDisplay, 0, 1, 0);
    return 1;
}
```

## See also

#### Reference

[Excel4/Excel12](excel4-excel12.md)
#### Concepts

[Functions in the Framework Library](functions-in-the-framework-library.md)

