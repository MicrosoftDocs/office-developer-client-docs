---
title: "xlCoerce"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlCoerce
keywords:
- xlcoerce function [excel 2007]
 
localization_priority: Normal
ms.assetid: 9d47c16c-a7e7-4998-b594-9cf001827b7b
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlCoerce

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Converts one type of **XLOPER**/ **XLOPER12** to another, or looks up cell values on a sheet. 
  
```cs
Excel12(xlCoerce, LPXLOPER12 pxRes, 2, LPXLOPER12 pxSource, LPXLOPER12 pxDestType);
```

## Parameters

 _pxSource_
  
The source **XLOPER**/ **XLOPER12** that needs to be converted. 
  
 _pxDestType_ ( **xltypeInt**)
  
(Optional). A bit-mask of the resulting types you are willing to accept. You should use the bitwise **OR** operator ( | ) to specify multiple possible types. If this argument is omitted, references to single cells are converted to one of the value types **xltypeStr**, **xltypeNum**, **xltypeBool**, **xltypeErr**, **xltypeNil** (if the referred-to cell is empty), and references to blocks of cells are converted to **xltypeMulti**. This makes **xlCoerce** the most convenient way to look up cell values. 
  
## Property Value/Return Value

Returns the coerced value ( **xltypeStr**, **xltypeNum**, **xltypeBool**, **xltypeErr**, **xltypeNil**, or **xltypeMulti**).
  
## Remarks

 **xlCoerce** cannot convert to or from **xltypeBigData** or **xltypeFlow**. Passing an **xltypeMissing** or **xltypeNil** type as  _pxDestType_ is equivalent to omitting the argument. Conversion can fail in some cases. For example, some strings cannot be converted to numbers, whereas others can. 
  
If an array or a multi-cell reference is converted to a single value type, the result is the value of the top left cell or array element.
  
## Example

The following code can be found in  `\SAMPLES\EXAMPLE\EXAMPLE.C`. 
  
> [!NOTE]
> The **xlcAlert** function implicitly tries to convert its argument to a string so that the coercion step shown here could in fact be removed, and **xInt** could be passed directly to **xlcAlert**. As **xlcAlert** is a command macro, this code only works correctly when called from a macro sheet. 
  
```cs
short WINAPI xlCoerceExample(short iVal)
{
   XLOPER12 xStr, xInt, xDestType;
   xInt.xltype = xltypeInt;
   xInt.val.w = iVal;
   xDestType.xltype = xltypeInt;
   xDestType.val.w = xltypeStr;
   Excel12f(xlCoerce, &xStr, 2, (LPXLOPER12)&xInt, (LPXLOPER12)&xDestType);
   Excel12f(xlcAlert, 0, 1, (LPXLOPER12)&xStr);
   Excel12f(xlFree, 0, 1, (LPXLOPER12)&xStr);
   return 1;
}
```

## See also

#### Reference

[xlSet](xlset.md)
#### Concepts

[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

