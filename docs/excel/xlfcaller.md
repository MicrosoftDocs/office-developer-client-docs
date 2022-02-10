---
title: "xlfCaller"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlfCaller
keywords:
- xlfcaller function [excel 2007]
 
ms.localizationpriority: medium
ms.assetid: de4b119c-ae2e-4207-9783-8d5692a4d052

---

# xlfCaller

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Returns information about the cell, range of cells, command on a menu, tool on a toolbar, or object that called the DLL command or function that is currently running.
  
|**Code called from**|**Returns**|
|:-----|:-----|
|DLL  <br/> |The Register ID. |
|A single cell  <br/> |A single-cell reference. |
|A multi-cell array formula  <br/> |A multi-cell reference. |
|A conditional formatting expression  <br/> |A reference to the cell to which the formatting condition is applied. |
|A menu  <br/> | A four-element single-row array:  <br/>  The bar ID.  The menu position.  The submenu position.  The command position. |
|A toolbar  <br/> | A two-element single-row array:  <br/>  The toolbar number for built-in toolbars or the toolbar name for custom toolbars.  The position on the toolbar. |
|A graphic object  <br/> |The object identifier (object name). |
|A command associated with an xlcOnEnter, ON.ENTER, event trap  <br/> |A reference to the cell or cells being entered. |
|A command associated with an xlcOnDoubleclick, ON.DOUBLECLICK, event trap. |The cell that was double-clicked (not necessarily the active cell). |
|Auto_Open, AutoClose, Auto_Activate or Auto_Deactivate macro  <br/> |The name of the calling sheet. |
|Other methods not listed  <br/> |#REF! Error. |
   
```cs
Excel12(xlfCaller, (LPXLOPER12) pxRes,0);
```

## Property value/Return value

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
   Excel12(xlfCaller, &xRes, 0);
   Excel12(xlcSelect, 0, 1, (LPXLOPER12)&xRes);
   Excel12(xlFree, 0, 1, (LPXLOPER12)&xRes);
   return 1;
}
```

## See also



[Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)

