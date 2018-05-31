---
title: "Evaluating names and other worksheet formula expressions"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- expression evaluation [excel 2007],worksheets [Excel 2007], name evaluation,evaluating expressions [Excel 2007],evaluating worksheet names [Excel 2007],expressions [Excel 2007], evaluating,names [Excel 2007], evaluating,name evaluation [Excel 2007],strings [Excel 2007], converting to values,xlfEvaluate function [Excel 2007],worksheets [Excel 2007], expression evaluation
localization_priority: Normal
ms.assetid: 2b23c75e-2a95-4f26-8714-2a73f5e326a7
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Evaluating names and other worksheet formula expressions

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
One of the most important features that Excel exposes through the C API is the ability to convert any string formula that can legally be entered into a worksheet to a value, or array of values. This is essential for XLL functions and commands that must read the contents of defined names, for example. This ability is exposed through the [xlfEvaluate function](xlfevaluate.md), as shown in this example.
  
```C
int WINAPI evaluate_name_example(void)
{
  wchar_t *expression = L"\016!MyDefinedName";
  XLOPER12 xNameText, xNameValue;
  xNameText.xltype = xltypeStr;
  xNameText.val.str = expression;
// Try to evaluate the name. Will fail with a #NAME? error
// if MyDefinedName is not defined in the active workbook.
  Excel12(xlfEvaluate, &xNameValue, 1, &xNameText);
// Attempt to convert the value to a string and display it in
// an alert dialog. This fails if xNameValue is an error value.
  Excel12(xlcAlert, 0, 1, &xNameValue);
// Must free xNameValue in case MyDefinedName evaluated to a string
  Excel12(xlFree, 0, 1, &xNameValue);
  return 1;
}
```

Note that when you are evaluating a worksheet name, either on its own or in a formula, you must prefix the name with '!', at least. Otherwise, Excel tries to find the name in a hidden namespace reserved for DLLs. You can create and delete hidden DLL names using the [xlfSetName function](xlfsetname.md). You can get the definition of any defined name, whether it is a hidden DLL name or a worksheet name, using the **xlfGetDef** function. 
  
The full specification for a worksheet name takes the following form:
  
`='C:\example folder\[Book1.xls]Sheet1'!Name`
  
Note that Excel 2007 introduced a number of new file extensions. You can omit the path, the workbook name, and the sheet name where there is no ambiguity among the open workbooks in this Excel session. 
  
The next example evaluates the formula  `COUNT(A1:IV65536)` for the active worksheet and displays the result. Note the need to prefix the range address with '!', which is consistent with the range reference convention on XLM macro sheets. The C API XLM follows this convention: 
  
- `=A1` A reference to cell A1 on the current macro sheet. (Not defined for XLLs). 
  
- `=!A1` A reference to cell A1 on the active sheet (which could be a worksheet or macro sheet) 
  
- `=Sheet1!A1` A reference to cell A1 on the specified sheet, Sheet1 in this case. 
  
- `=[Book1.xls]Sheet1!A1` A reference to cell A1 on the specified sheet in the specified workbook. 
  
In an XLL, a reference without a leading exclamation point (**!**) cannot be converted to a value. It has no meaning because there is no current macro sheet. Note that a leading equals sign (**=**) is optional and is omitted in the next example.
  
```C
int WINAPI evaluate_expression_example(void)
{
    wchar_t *expression = L"\022COUNT(!A1:IV65536)";
    XLOPER12 xExprText, xExprValue;
    xExprText.xltype = xltypeStr;
    xExprText.val.str = expression;
// Try to evaluate the formula.
    Excel12(xlfEvaluate, &xExprValue, 1, &xExprText);
// Attempt to convert the value to a string and display it in
// an alert dialog. Will fail if xExprValue is an error.
    Excel12(xlcAlert, 0, 1, &xExprValue);
// Not strictly necessary, as COUNT never returns a string
// but does no harm.
    Excel12(xlFree, 0, 1, &xExprValue);
    return 1;
}
```

You can also use the **xlfEvaluate** function to retrieve the registration ID of an XLL function from its registered name, which can then be used to call that function using the [xlUDF function](xludf.md).
  
> [!NOTE]
> The registered name can be passed directly to the **xlUDF** function. This means that you can avoid having to evaluate the name to get the ID before calling **xlUDF**. However, if the function is to be called many times, calling it by using the registration ID is faster. 
  
## See also

- [Excel Worksheet and Expression Evaluation](excel-worksheet-and-expression-evaluation.md)
- [Permitting User Breaks in Lengthy Operations](permitting-user-breaks-in-lengthy-operations.md)
- [Getting Started with the Excel XLL SDK](getting-started-with-the-excel-xll-sdk.md)

