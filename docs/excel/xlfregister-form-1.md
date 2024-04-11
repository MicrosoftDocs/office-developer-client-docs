---
title: "xlfRegister (Form 1)"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- xlfRegister
keywords:
- xlfregister function [excel 2007]
ms.localizationpriority: medium
ms.assetid: c730124c-1886-4a0f-8f06-79763025537d

---

# xlfRegister (Form 1)

**Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
Can be called from a DLL or XLL command that has itself been called by Microsoft Excel. This is equal to calling **REGISTER** from an Excel XLM macro sheet.
  
**xlfRegister** can be called in two forms:
  
- xlfRegister (Form 1): Registers a single command or function.

- [xlfRegister (Form 2)](xlfregister-form-2.md): Loads and activates an XLL.

Called in Form 1, this function makes a DLL function or command available to Excel, sets its use count to 1, and returns its registration ID, which can be used to call the function later by using the [xlUDF](xludf.md) or the **xlfCall** function. The registration ID is also used to unregister the function using [xlfUnregister (Form 1)](xlfunregister-form-1.md). If the function has been registered, calling **xlfRegister** again increments its use count.
  
This form of the function also defines a hidden name which is the function text argument, _pxFunctionText_, and which evaluates to the registration ID of the function or command. When you unregister the function, delete this name using the [xlfSetName](xlfsetname.md). For more information, see [Known Issues in Excel XLL Development](known-issues-in-excel-xll-development.md).
  
```cs
Excel12(xlfRegister, LPXLOPER12 pxRes, int iCount,
    LPXLOPER12 pxModuleText,   LPXLOPER12 pxProcedure,
    LPXLOPER12 pxTypeText,     LPXLOPER12 pxFunctionText,
    LPXLOPER12 pxArgumentText, LPXLOPER12 pxMacroType,
    LPXLOPER12 pxCategory,     LPXLOPER12 pxShortcutText,
    LPXLOPER12 pxHelpTopic,    LPXLOPER12 pxFunctionHelp,
    LPXLOPER12 pxArgumentHelp1, LPXLOPER12 pxArgumentHelp2,
        ...);
```

## Parameters

_pxModuleText_ (**xltypeStr**)
  
The name of the DLL that contains the function. This can be obtained by calling the XLL-only function [xlGetName](xlgetname.md) if the function registered is also within the currently executing DLL.
  
_pxProcedure_ (**xltypeStr** or **xltypeNum**)
  
If a string, the name of the function to call as it appears in the DLL code. If a number, the ordinal export number of the function to call. For clarity, always use the string form.
  
_pxTypeText_ (**xltypeStr**)
  
An optional string that specifies the types of arguments to the function and the type of the return value of the function. For more information, see the Remarks section. This argument can be omitted for a stand-alone DLL (XLL) that includes an [xlAutoRegister function](xlautoregister-xlautoregister12.md) or **xlAutoRegister12**.
  
> [!NOTE]
> **xlAutoRegister12** is only supported in Excel 2007.
  
If **xlfRegister** is called with this argument missing, Excel calls **xlAutoRegister** or **xlAutoRegister12**, if either exists in the specified DLL, which should then correctly register the function by providing this information.
  
_pxFunctionText_ (**xltypeStr**)
  
The function name as it will appear in the Function Wizard. This argument is optional; if it is omitted, the function is not available in the Function Wizard, and can only be called using the **CALL** function using the functions registration ID from an XLM macro sheet. Therefore, for ordinary worksheet use, you should handle this argument as required.
  
_pxArgumentText_ (**xltypeStr**)
  
An optional text string that describes the arguments to the function. The user sees this in the Function Wizard. If it is omitted, Excel constructs basic descriptions from _pxTypeText_.
  
_pxMacroType_ (**xltypeNum** or **xltypeInt**)
  
An optional argument that indicates the type of XLL entry point. The default value, if it is omitted, is 1.
  
| _pxMacroType value_ <br/> |0  <br/> |1  <br/> |2  <br/> |
|:-----|:-----|:-----|:-----|
|Can be called from a worksheet  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Can be called from a macro sheet  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Can be called from a defined name definition  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Can be called from a conditional format expression  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Listed in the Function Wizard for worksheet functions  <br/> |No  <br/> |Yes  <br/> |No  <br/> |
|Listed in the Function Wizard for macro sheet functions  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |

In practice, you should use 1 for worksheet functions, 1 for macro sheet equivalent functions (registered as type **#**) that you want to call from the worksheet, and 2 for commands.
  
> [!NOTE]
> XLL commands are hidden and not displayed in dialog boxes for running macros, although their names can be entered anywhere a valid command name is required.
  
_pxCategory_ (**xltypeStr** or **xltypeNum**)
  
An optional argument that enables you to specify which category that the new function or command should belong to. The Function Wizard divides functions by type (category). You can specify a category name or a sequential number, where the number is the position in which the category appears in the Function Wizard. For more information, see the "Category Names" section. If it is omitted, the User Defined category is assumed.
  
_pxShortcutText_ (**xltypeStr**)
  
A one-character, case-sensitive string that specifies the control key assigned to this command. For example, "A" assigns this command to CONTROL+SHIFT+A. This argument is optional and is used for commands only.
  
_pxHelpTopic_ (**xltypeStr**)
  
An optional reference to the Help file (.chm or .hlp) to display when the user clicks the Help button (when your custom function is displayed). Can be in the form `filepath!HelpContextID` or `https://address/path_to_file_in_site!0`. Both parts before and after the "!" are required. _HelpContextID_ must not contain single quotes, and will be converted by Excel to an unsigned integer 4 bytes long, in decimal form. When using the URL form, Excel opens only the referenced help file.
  
_pxFunctionHelp_ (**xltypeStr**)
  
An optional string that describes your custom function when it is selected in the Function Wizard.
  
_pxArgumentHelp1_ (**xltypeStr**)
  
Optional. The first of the strings that describe the custom arguments of the function when the function is selected in the Function Wizard. In Excel 2003 and earlier, **xlfRegister** can take, at most, 30 arguments so that you can provide this help for the first 20 of your function arguments only. Starting in Excel 2007, **xlfRegister** can take up to 255 arguments so that you can provide this help for up to 245 function parameters.
  
## Property value/Return value

If registration was successful, this function returns the register ID of the function (**xltypeNum**), which can be used in calls to **xlUDF** and **xlfUnregister** in a DLL, or with **CALL** and **UNREGISTER** in an XLM macro sheet. Otherwise, it returns a #VALUE! error.
  
## Remarks

### Data types

The _pxTypeText_ argument specifies the data type of the return value and the data types of all arguments to the DLL function or code resource. The first character of _pxTypeText_ specifies the data type of the return value. The remaining characters indicate the data types of all the arguments. For example, a DLL function that returns a floating-point number and takes an integer and a floating-point number as arguments would require "BIB" for the _pxTypeText_ argument.
  
The data types and structures used by Excel to exchange data with XLLs are summarized in the following two tables.
  
The first table lists the types supported in all versions of Excel.
  
|**Data type**|**Pass by value**|**Pass by ref (pointer)**|**Comments**|
|:-----|:-----|:-----|:-----|
|Boolean  <br/> |A  <br/> |L  <br/> |short [int] (0=false or 1=true)  <br/> |
|double  <br/> |B  <br/> |E  <br/> ||
|char \*  <br/> ||C, F  <br/> |Null-terminated ASCII byte string  <br/> |
|unsigned char \*  <br/> ||D, G  <br/> |Counted ASCII byte string  <br/> |
|unsigned short [int]  <br/> |H  <br/> ||16-bit WORD  <br/> |
|[signed] short [int]  <br/> |I  <br/> |M  <br/> |16-bit signed integer  <br/> |
|[signed long] int  <br/> |J  <br/> |N  <br/> |32-bit signed integer  <br/> |
|FP  <br/> ||K  <br/> |Floating-point array structure  <br/> |
|Array  <br/> ||O  <br/> |Three arguments are passed:<br/>- unsigned short int \*<br/>- unsigned short int \*<br/>- double []  <br/> |
|XLOPER  <br/> ||P  <br/> |Variable-type worksheet values and arrays  <br/> |
||Value |R  <br/> |Values, arrays, and range references  <br/> |

In Excel 2007 the following data types were introduced to support the larger grids and long Unicode strings.
  
|**Data type**|**Pass by value**|**Pass by ref (pointer)**|**Comments**|
|:-----|:-----|:-----|:-----|
|unsigned short \*  <br/> ||C%, F%  <br/> |Null-terminated Unicode wide-character string  <br/> |
|unsigned short \*  <br/> ||D%, G%  <br/> |Counted Unicode wide-character string  <br/> |
|FP12  <br/> ||K%  <br/> |Larger grid floating-point array structure  <br/> |
|Array  <br/> ||O%  <br/> |Three arguments are passed:<br/>- signed int \* / RW \*<br/>- signed int \* / COL \*<br/>- double []  <br/> |
|XLOPER12  <br/> ||Q  <br/> |Variable-type worksheet values and arrays  <br/> |
||Value |U  <br/> |Values, arrays, and range references  <br/> |

Starting in Excel 2010 the following data types were introduced:
  
|**Data Type**|**Pass by value**|**Pass by ref (pointer)**|**Comments**|
|:-----|:-----|:-----|:-----|
|XLOPER12  <br/> ||X  <br/> |The asynchronous handle is used to track a pending asynchronous function call by Excel and the XLL.The existence of the parameter type in the type string also designates the function as asynchronous.For more information about asynchronous functions, see [Asynchronous User-Defined Functions](asynchronous-user-defined-functions.md). |

The string types **F**, **F%**, **G**, and **G%** are used for arguments that are modified-in-place.
  
When working with the data types displayed in the previous table, be aware of the following:
  
- The C-language declarations assume that your compiler uses 8-byte doubles, 2-byte short integers, and 4-byte long integers by default.
- All functions in DLLs and code resources are called using the **__stdcall** calling convention.
- Any function that returns a data type by reference, that is, that returns a pointer to something, can safely return a null pointer. Excel interprets a null pointer as a #NUM! error.

## Additional data type information

This section contains detailed information about the **E**, **F**, **F%**, **G**, **G%**, **K**, **O**, **P**, **Q**, **R**, and **U** data types, and other information about the _pxTypeText_ argument.
  
### E data type

Excel expects a DLL using the E data type to pass pointers to floating-point numbers on the stack. This can cause problems with some languages (for example, Borland C++) that expect the number to be passed on the coprocessor emulator stack. The workaround is to pass a pointer to the number on the coprocessor stack. The following example shows how to return a double from Borland C++.
  
```cpp
typedef double * lpDbl;
extern "C" lpDbl __stdcall AddDbl(double D1,
    double D2, WORD npDbl)
{
    lpDbl Result;
    Result = (lpDbl)MK_FP(_SS, npDbl);
    *Result = D1 + D2;
    return (Result);
}
```

### F, F%, G, and G% data types

With the **F**, **F%**, **G**, and **G%** data types, a function can modify a string buffer that is allocated by Excel. If the return value type code is one of these types, Excel ignores the value returned by the function. Instead, Excel searches the list of function arguments for the first corresponding data type (**F**, **F%**, **G**, or **G%**) and then takes the current contents of the allocated string buffer as the return value. All versions of Excel allocate 256 bytes for **F** and **G** ASCII strings, and starting in Excel 2007 65,536 bytes are allocated, enough for 32,768 Unicode characters, for **F%** and **G%** Unicode strings. Remember that the buffers must include a count character (types **G** and **G%**) or a null-termination character (types **F** and **F%**), so that the actual maximum string lengths are 255 and 32,767. Unicode strings, and therefore type **F%** and **G%** arguments, are available only through the C API in Excel.
  
### K and K% data types

The **K** and **K%** data types use pointers to the variable-sized FP and FP12 structures respectively. These structures are defined in XLLCALL.H. FP12 structures, and therefore type **K%** arguments, are only supported starting in Excel 2007.
  
### O and O% data types

The **O** and **O%** data types can only be used for arguments, not return values, although values can be returned my modifying an **O** or **O%** type argument in place. Each passes three items: a pointer to the number of rows in an array, a pointer to the number of columns in an array, and a pointer to a two-dimensional array of floating-point numbers.
  
To modify an array passed by the O or O% data type in place, you could use ">O" or ">O%" as the _pxTypeText_ argument. For more information about modifying an array, see the "Modifying in Place: Functions Declared as Void" section in this topic.
  
The **O** data type was created for direct compatibility with Fortran DLLs, which pass arguments by reference.
  
The **O%** is supported starting in Excel 2007, and accommodates the larger number of rows that Excel supports.
  
### P and Q data types

When DLL function arguments are registered as taking type **P** XLOPERs or type **Q** XLOPER12s, Excel converts single-cell references to simple values and multi-cell references to arrays when preparing these arguments. In other words, **P** and **Q** types will always arrive in your function as one of these types: **xltypeNum**, **xltypeStr**, **xltypeBool**, **xltypeErr**, **xltypeMulti**, **xltypeMissing**, or **xltypeNil**, but not **xltypeRef** or **xltypeSRef** because these are always dereferenced. **XLOPER12**s, and therefore type **Q** arguments, are only supported starting in Excel 2007.
  
If types **xltypeMissing** or **xltypeNil** are used for return values, they are interpreted by Excel as numeric zero. **xltypeMissing** is passed when the caller omits an argument. **xltypeNil** is passed when the caller passes a reference to an empty cell. When a range of cells is converted to an **xltypeMulti** to be passed as type **P** or **Q**, any blank cells within the range are converted to **xltypeNil** array elements. Missing elements in a literal array are similarly passed as **xltypeNil** elements.
  
### Volatile functions and recalculation

On a worksheet, you can make a DLL function or code resource volatile, so that it recalculates every time the worksheet recalculates. To do this, add an exclamation mark (!) after the last argument code in the _pxTypeText_ argument.

> [!NOTE]
> By default, functions that take type **R** XLOPERs or type **U** XLOPER12s and that are registered as macro sheet equivalents (type **#**; see next section) are handled as volatile in Excel.
  
### Functions declared as void

There are two cases that call for declaring a function as returning void. In both cases, the function returns its result by other means.
  
#### Modifying in place

You can use a single digit _n_ for the return type code in _pxTypeText_, where _n_ is a number from 1 through 9. This instructs Excel to take the value of the variable in the location pointed to by the _n_th argument in_pxTypeText_as the return value. This is also known as modifying in place. The_n_th argument must be a pass-by-reference data type (C, D, E, F, F%, G, G%, K, K%, L, M, N, O, O%, P, Q, R, or U). The DLL function or code resource must also be declared with the **void** keyword in the C/C++ languages (or the **procedure** keyword in the Pascal language).
  
For example, a DLL function that takes a null-terminated string and two pointers to integers as arguments can modify the string in place. Use "1FMM" as the _pxTypeText_ argument, and declare the function as void.
  
Previous versions of Excel used **\>** at the start of _pxTypeText_ to signify that the function was declared as void and that the first argument was to be modified in place—there was no way to modify any argument other than the first. The **\>** is equivalent to _n_ = 1 in current Excel versions and this use of **\>** in synchronous functions is supported for backward compatibility only.

#### Asynchronous functions

An asynchronous function, denoted by using a parameter of type X in **pxTypeText**, does not return its result from the initial function call. Instead, you must declare an asynchronous function as void and later the add-in returns the result through a callback. The asynchronous function must be registered by using **\>** at the start of **pxTypeText**. In asynchronous functions, **\>** denotes that the function is declared as void, but does not indicate that the first argument is modified in place. For more information about asynchronous functions, see [Asynchronous User-Defined Functions](asynchronous-user-defined-functions.md).

### Registering worksheet functions as macro sheet equivalents (handling uncalculated cells)

Placing a **#** character after the last parameter code in _pxTypeText_ gives the function the same calling permissions as functions on a macro sheet. These are as follows:
  
- The function can retrieve the values of cells that have not yet been calculated in this recalculation cycle.

- The function can call any of the XLM information (Class 2) functions, for example, **xlfGetCell**.

- If the number sign (#) is not present: evaluating an uncalculated cell results in an **xlretUncalced** error, and the current function is called again once the cell has been calculated; calling any XLM information function other than **xlfCaller** results in an **xlretInvXlfn** error.

### Registering worksheet functions as thread-safe

Starting in Excel 2007, Excel can perform multithreaded workbook recalculation. This means that it can assign different instances of a thread-safe function to concurrent threads for reevaluation. Starting in Excel 2007, most of the built-in worksheet functions are thread-safe. Starting in Excel 2007, Excel also allows XLLs to register worksheet functions as thread-safe. To do this, include a **$** character after the last parameter code in _pxTypeText_.
  
> [!NOTE]
> Only worksheet functions can be declared as thread-safe. Excel does not consider a macro sheet equivalent function to be thread-safe, so that you cannot append both **#** and **$** characters to the _pxTypeText_ argument.
  
If you have registered a function as thread-safe, you must ensure that it behaves in a thread-safe way, although Excel rejects any thread-unsafe calls via the C API. For example, if a thread-safe function tries to call **xlfGetCell**, the call fails with the **xlretNotThreadSafe** error.
  
### Registering worksheet functions as cluster-safe

Starting in Excel 2010, Excel can offload function calls to a designated compute cluster provider. For more information, see [Cluster Safe Functions](cluster-safe-functions.md). Any XLL worksheet functions registered as cluster-safe take part in offloading if a cluster is available. Cluster-safe functions are registered by including the **&amp;** character after the last parameter code in the _pxTypeText_ argument.
  
If you have registered a function as cluster-safe, you must ensure that it behaves in a cluster-safe way. For more information, see [Cluster Safe Functions](cluster-safe-functions.md).
  
> [!NOTE]
> Only worksheet functions can be declared as cluster-safe. Excel does not consider a macro sheet equivalent function to be cluster-safe, so that you cannot append both **#** and **&amp;** characters to the _pxTypeText_ argument. Worksheet functions can be declared as both cluster-safe and thread-safe. In this case, Excel will allow these functions to take part in multithreaded recalculation when cluster offloading is disabled.
  
### Category names

Use the following guidelines to determine which category to put your XLL functions in.
  
- If the function does something that could be done by the user as a part of your add-in user interface, you should put the function in the **Commands** category.
- If the function returns information about the state of the add-in or any other useful information, you should put the function in the **Information** category.
- An add-in should never add functions or commands to the **User Defined** category. This category is for the exclusive use of end users.

-The category is specified using the _pxCategory_ parameter to **xlfRegister**. This can be a number or text that corresponds to one of the hard-coded standard categories, or the text of a new category specified by the DLL. If the text given does not already exist, Excel creates a new category with that name.
  
The following table lists the standard categories that are visible when you view the **Paste Function** dialog box from within a worksheet.
  
|**Number**|**Text**|
|:-----|:-----|
|1  <br/> |Financial  <br/> |
|2  <br/> |Date &amp; Time  <br/> |
|3  <br/> |Math &amp; Trig  <br/> |
|4  <br/> |Text  <br/> |
|5  <br/> |Logical  <br/> |
|6  <br/> |Lookup &amp; Reference  <br/> |
|7  <br/> |Database  <br/> |
|8  <br/> |Statistical  <br/> |
|9  <br/> |Information  <br/> |
|14  <br/> |User Defined  <br/> |
||Engineering (starting in Excel 2007)  <br/> |
||Cube (starting in Excel 2007)  <br/> |

In addition, these categories are also visible when you view the **Paste Function** dialog box from within a macro sheet.
  
|**Number**|**Text**|
|:-----|:-----|
|10  <br/> |Commands  <br/> |
|11  <br/> |DDE/External  <br/> |
|12  <br/> |Customizing  <br/> |
|13  <br/> |Macro Control  <br/> |

### Example

See the code for the **xlAutoOpen** function in `\SAMPLES\GENERIC\GENERIC.C`.
  
## See also

- [REGISTER.ID](xlfregisterid.md)
- [UNREGISTER](xlfunregister-form-1.md)
- [Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)
