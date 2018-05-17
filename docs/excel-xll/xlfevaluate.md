---
title: "xlfEvaluate"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlfEvaluate
keywords:
- xlfevaluate function [excel 2007]
 
localization_priority: Normal
ms.assetid: deea3ee6-2a32-47ef-bfa4-914891538633
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlfEvaluate

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Uses the Microsoft Excel parser and function evaluator to evaluate any expression that could be entered in a worksheet cell.
  
```cs
Excel12(xlfEvaluate, LPXLOPER12 pxRes, 1, LPXLOPER12 pxFormulaText);
```

## Parameters

 _pxFormulaText (xltypeStr)_
  
The string to be evaluated. A leading equal sign (=) is optional. The string can be any text that can legally be entered into a worksheet or macro sheet cell.
  
## Property Value/Return Value

Returns the result of evaluating the string which can be any of the types **xltypeNum**, **xltypeStr**, **xltypeBool**, **xltypeErr**, **xltypeNil**, **xltypeMulti**.
  
## Remarks

The string can contain only functions, not command equivalents. It is equivalent to pressing **F9** from the formula bar. If **xlfEvaluate** is called from an XLL worksheet function that has been registered as thread safe, the expression must only contain thread-safe functions. 
  
The primary use of the **xlfEvaluate** function is to allow DLLs to find out the value assigned to a defined name that is either on a sheet or a hidden name defined within the DLL. Note that within a DLL/XLL, a worksheet name must be prefixed with at least an exclamation mark (!) to ensure that it is interpreted as external to the DLL. For more information, see [Evaluating Names and Other Worksheet Formula Expressions](evaluating-names-and-other-worksheet-formula-expressions.md).
  
 **xlfEvaluate** cannot be used to evaluate references to an external sheet that is not open. 
  
## Example

This example uses **xlfEvaluate** to coerce the text "!B38" to the contents of cell B38. 
  
 `\SAMPLES\EXAMPLE\EXAMPLE.C`. This function calls a command macro ( **xlcAlert**) and will work correctly only when called from a macro sheet or as a macro command.
  
```cs
short WINAPI EvaluateExample(void)
{
    XLOPER12 xFormulaText, xRes, xRes2, xInt;
    xFormulaText.xltype = xltypeStr;
    xFormulaText.val.str = L"\004!B38";
    Excel12(xlfEvaluate, &amp;xRes, 1, (LPXLOPER12)&amp;xFormulaText);
    xInt.xltype = xltypeInt;
    xInt.val.w = 2;
    Excel12(xlcAlert, &amp;xRes2, 2, (LPXLOPER12)&amp;xRes, (LPXLOPER12)&amp;xInt);
    Excel12(xlFree, 0, 1, (LPXLOPER12)&amp;xRes);
    Excel12(xlFree, 0, 1, (LPXLOPER12)&amp;xRes2);
    return 1;
}
```

## See also

#### Concepts

[Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)

