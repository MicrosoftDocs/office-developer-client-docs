---
title: "xlfCaller"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlfCaller
keywords:
- xlfcaller function [excel 2007]
 
localization_priority: Normal
ms.assetid: de4b119c-ae2e-4207-9783-8d5692a4d052
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlfCaller

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Returns information about the cell, range of cells, command on a menu, tool on a toolbar, or object that called the DLL command or function that is currently running.
  
|**Code called from**|**Returns**|
|:-----|:-----|
|DLL  <br/> |The Register ID.  <br/> |
|A single cell  <br/> |A single-cell reference.  <br/> |
|A multi-cell array formula  <br/> |A multi-cell reference.  <br/> |
|A conditional formatting expression  <br/> |A reference to the cell to which the formatting condition is applied.  <br/> |
|A menu  <br/> | A four-element single-row array:  <br/>  The bar ID.  <br/>  The menu position.  <br/>  The submenu position.  <br/>  The command position.  <br/> |
|A toolbar  <br/> | A two-element single-row array:  <br/>  The toolbar number for built-in toolbars or the toolbar name for custom toolbars.  <br/>  The position on the toolbar.  <br/> |
|A graphic object  <br/> |The object identifier (object name).  <br/> |
|A command associated with an xlcOnEnter, ON.ENTER, event trap  <br/> |A reference to the cell or cells being entered.  <br/> |
|A command associated with an xlcOnDoubleclick, ON.DOUBLECLICK, event trap.  <br/> |The cell that was double-clicked (not necessarily the active cell).  <br/> |
|Auto_Open, AutoClose, Auto_Activate or Auto_Deactivate macro  <br/> |The name of the calling sheet.  <br/> |
|Other methods not listed  <br/> |#REF! Error.  <br/> |
   
```cs
Excel12(xlfCaller, (LPXLOPER12) pxRes,0);
```

## Property Value/Return Value

The return value is one of the following **XLOPER**/ **XLOPER12** data types: **xltypeRef**, **xltypeSRef**, **xltypeNum**, **xltypeStr**, **xltypeErr**, or **xltypeMulti**. Since three of these types point to allocated memory, the return value of **xlfCaller** should always be freed in a call to the [xlFree function](xlfree.md) when it is no longer needed. 
  
For more information about **XLOPERs**/ **XLOPER12s** see [Memory Management in Excel](memory-management-in-excel.md).
  
## Remarks

This function is the only non-worksheet function that can be called from a DLL/XLL worksheet function. Other XLM information functions can only be called from commands or macro-sheet equivalent functions.
  
## Example

 `\SAMPLES\EXAMPLE\EXAMPLE.C`. This function calls a command macro (xlcSelect) and will work correctly only when called from a macro sheet.
  
```cs
short WINAPI CallerExample(void)
{
   XLOPER12 xRes;
   Excel12(xlfCaller, &amp;xRes, 0);
   Excel12(xlcSelect, 0, 1, (LPXLOPER12)&amp;xRes);
   Excel12(xlFree, 0, 1, (LPXLOPER12)&amp;xRes);
   return 1;
}
```

## See also

#### Concepts

[Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)

