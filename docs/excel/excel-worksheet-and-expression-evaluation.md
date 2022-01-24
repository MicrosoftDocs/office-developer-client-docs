---
title: "Excel Worksheet and Expression Evaluation"
manager: lindalu
ms.date: 01/22/2022
ms.audience: Developer
ms.topic: overview
keywords:
- expression evaluation [excel 2007],errors in worksheets [Excel 2007],long Unicode strings [Excel 2007],evaluating expressions [Excel 2007],evaluating worksheets [Excel 2007],worksheet evaluation [Excel 2007],worksheet errors [Excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 47b46a7d-6cfb-4f5b-946d-e0164d18512a

---

# Excel Worksheet and Expression Evaluation

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
Microsoft Excel worksheet cell contents are evaluated into one of four basic data types:
  
- **Numbers**
- **Boolean TRUE** or **FALSE**
- **Strings**
- **Errors**

Mixed-type arrays of these types can also be entered into formulas as arguments to functions or as values spanning more than one cell in an array formula.
  
When a user (or a command macro) enters something into a cell, Excel tries to interpret the input and displays an error message if it cannot. If the input starts with a string prefix (a single quotation mark) Excel places all the input characters in the cell as provided, with no modification. (The string prefix is not displayed.) If the input begins with **=**, **+**, or **-**, Excel tries to interpret the input as a formula.If the syntax is incorrect or evaluation is stopped, an error is displayed, and the cell is put in edit mode. Otherwise, Excel tries to identify, convert, and evaluate operators and function names and their arguments.
  
Operands are evaluated from left to right before the operator is applied. Functions are evaluated starting with the highest-precedence operators and innermost (most nested). If function arguments or operands cannot be converted to the types expected, evaluation fails and results in a **#VALUE!** error. When a token (that is not a literal value) is not recognized as a function or defined name or label, evaluation fails and results in a **#NAME?** error.
  
If the input does not start with any of these things, Excel checks against known patterns of input such as dates, times, currency amounts, percentages, or numbers, and interprets accordingly. This is done in a locale-specific way. If none of these interpretations makes sense, Excel reverts to considering the input as a string and places it in the cell unchanged.
  
Excel supports other data types, the most visible of which is a range reference. Excel converts references to the values of the referred-to cells when evaluating arguments for operators and functions that do not take reference arguments, or when the expression in a cell formula reduces to a reference.
  
Excel exposes the ability to reduce any valid character string to one of the basic four worksheet data types with the XLM function **EVALUATE** and its C API equivalent **xlfEvaluate**. This function provides, among other things, a simple way to evaluate named ranges in DLL code. This function differs from the behavior described earlier only in that instead of displaying error messages or enabling cell editing, it returns a **#VALUE!** error if the expression evaluation fails.
  
## Numbers

All worksheet numbers in Excel are represented internally as 8-byte double-precision floating point, including all integers. However, the implementation of these numbers in Excel is not fully IEEE compliant, as shown in the following table.
  
|**Type**|**Maximum**|**Minimum**|
|:-----|:-----|:-----|
|IEEE 8-byte double  <br/> |1.7976931348623157E+308  <br/> |2.2250738585072014E-308  <br/> |
|Worksheet (returned by function or paste value)  <br/> |1.7976931348623157E+308  <br/> |2.22507385850721E-308  <br/> |
|Worksheet (manual input)  <br/> |9.99999999999999E+307  <br/> |2.22507385850721E-308  <br/> |

IEEE subnormal numbers (that is, numbers in the range 2.2250738585072009E-308 to 4.9406564584124654E-324) are not supported in Excel worksheets but are supported by VBA Doubles.
  
If a DLL function returns IEEE +/- infinity or an invalid double, Excel converts it to **#NUM!**. All subnormal numbers and numbers smaller than the minimum positive normal in Excel are converted to positive zero. IEEE negative zero is supported, that is, it can be returned by a DLL function and is displayed as **-0**. (The **\<** operator does not check for negative zero, and so **=A1\<0** evaluates to **TRUE** if A1 contains negative zero).
  
Note that certain number formats have narrower limits than these, for example, dates and times. Integer division is, in fact, floating point division and might, in extreme cases, yield a non-integer result where the precise result should be an integer.
  
## Long Unicode Strings

All strings the user sees in Excel have for many versions now been stored internally as Unicode strings.Unicode worksheet strings can be up to 32,767 (2<sup>15</sup> - 1) characters in length and can contain any valid Unicode character.
  
When the C API was first introduced, worksheet strings were byte strings limited in length to 255 characters, and the C API reflected these limitations. With Excel 2007, the C API is updated to handle Excel long Unicode strings.This means that DLL functions registered in the right way can accept Unicode arguments and return Unicode strings.
  
> [!NOTE]
> Byte strings are still fully supported in the C API for backward compatibility; however they still have the same 255-character limit.
  
## Returning Errors

Excel evaluates cells to errors where it cannot convert function or operator arguments to the correct type, or if it does not recognize a function or defined name. Both of these scenarios were described earlier. When the built-in worksheet functions and operators fail, they also result in errors that inform the user of the type of failure. You should have your own add-in functions return errors that are consistent with the behavior in Excel.
  
### #NULL!

The **#NULL!** error is returned by some XLM information functions. For example, calling **GET.DOCUMENT(78)**, or the equivalent C API function **xlfGetDocument** with argument 78, when there are no printers installed results in this error being returned. It can also be returned by some functions when, for example, they evaluate an empty string.
  
You might want to return this error from your add-in function when none of the other errors seems appropriate.
  
### #DIV/0!

The Excel division operator returns the **#DIV/0!** error when the denominator evaluates to zero or a number is too small to be represented as non-zero by Excel. Some functions that by definition involve a division can also return this error. For example, **AVERAGE** returns this error if none of the inputs can be converted to numbers.
  
You should only consider returning this error from your add-in function to indicate that a division by zero was detected.
  
### #VALUE!

Excel returns the **#VALUE!** error if a function or operator argument cannot be converted to the required type. In the case of function arguments that cannot be converted, for example `=LN("X")`, Excel does not call the function code. This is an important point to remember when writing and debugging your own add-in functions.
  
Some functions return this error if an argument cannot be converted within the function code. For example, `DATEVALUE("30-Feb-2007")` fails with this error despite the argument being of the right type. In this case, it is the function that is returning the error from within its code. Some functions return this error even though the value types and ranges are allowable, for example `FIND("a","xyz")` returns this error.
  
You should consider returning this error from your add-in function to indicate that the arguments are of the wrong type, could not be converted to the right type, or are out of range, although you should consider returning **#NUM!** for numerical arguments out of range. You should also consider returning this error when range or array arguments are the wrong shape or size.
  
### #REF!

Excel generates the **#REF!** error within an expression when it is copied to a location where the resulting relative reference goes out of bounds. For example, if the cell B2 contains the formula `=A1`, copying this to cell B1 results in a formula **=#REF!**. This error is also generated in formulas that contain a reference that is overwritten in a cut-and-paste operation or is deleted in a row, column, or worksheet deletion. Some functions that can return references can return this error, for example, `OFFSET(A1,-1,-1)`. Worksheet names whose definitions contain references that become invalid are evaluated to this error.
  
If your add-in function takes reference arguments, you should consider returning this error if the references are invalid, or if you are passed a reference error. The section on XLOPER/XLOPER12s in [Memory Management in Excel](memory-management-in-excel.md) describes how to create functions that can accept and return reference arguments.
  
### #NAME?

Excel generates the **#NAME?** error when an expression contains a token that is not recognized as a function or defined name. If your add-in function tries to access a defined name and it is not defined, you should consider returning this error.
  
### #NUM!

Many of the built-in numerical and mathematical functions in Excel return the **#NUM!** error when a numerical input is out of the permitted range, for example, `LN(0)`. You should consider returning this error from your add-in function to indicate that a numerical input was invalid or out of range.
  
### #N/A

The **#N/A** error is often returned to signify a successful or meaningful result is not available. For example, MATCH with the third argument zero returns this error if an exact match cannot be found. This error can also be generated using the function **NA** and specifically detected with the function **ISNA**. It is therefore a commonly used error in worksheets to indicate a range of application-specific conditions.
  
## See also

[Excel Programming Concepts](excel-programming-concepts.md)
  
[Programming with the C API in Excel](programming-with-the-c-api-in-excel.md)
  
[Evaluating Names and Other Worksheet Formula Expressions](evaluating-names-and-other-worksheet-formula-expressions.md)
  
[Excel XLL SDK API Function Reference](excel-xll-sdk-api-function-reference.md)
