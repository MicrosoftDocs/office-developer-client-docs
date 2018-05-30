---
title: "Data types used by Excel"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
keywords:
- registration data types [excel 2007],Excel data types,strings [Excel 2007],numbers [Excel 2007],data structures [Excel 2007],data types [Excel 2007]
localization_priority: Normal
ms.assetid: 8740a8fb-ad67-4232-a49b-d78967a786c2
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Data types used by Excel

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Microsoft Excel exchanges several ANSI C/C++ types and also some Excel-specific data structures. These are mentioned here to provide a context for other sections, and they are discussed in detail in the [xlfRegister (Form 1)](xlfregister-form-1.md) topic. 
  
## ANSI C/C++ types

### Numbers

All versions of Excel:
  
- 8-byte double
    
- [signed] short [int] &ndash; used for **Boolean** values and also integers 
    
- unsigned short [int]
    
- [signed long] int
    
### Strings

All versions of Excel:
  
- [signed] char \* &ndash; null-terminated byte strings of up to 255 characters
    
- unsigned char \* &ndash; length-counted byte strings of up to 255 characters
    
Starting in Excel 2007:
  
- unsigned short \* &ndash; Unicode strings of up to 32,767 characters, which can be null-terminated or length-counted
    
All worksheet numbers in Excel are stored as doubles so that it is not necessary (and in fact introduces a small conversion overhead) to declare add-in functions as exchanging integer types with Excel.
  
Where you are using integer types, Excel verifies that the inputs are within the limits of the type, and they fail with **#NUM!** if outside these. The exception is when you are registering a function to take a **Boolean** argument, implemented using short int. In this case, any non-zero input is converted to 1, and zero is passed straight through. 
  
## Excel-specific data structures

All versions of Excel:
  
- **FP** &ndash; a two-dimensional floating-point array structure supporting up to 65,356 rows by the maximum number columns supported in the given version of Excel. 
    
- **XLOPER** &ndash; a multi-type data structure that can represent all the worksheet data types (including errors), integers, range references, XLM macro sheet flow control types, and an internal binary storage data type. 
    
   > [!NOTE]
   > Strings are represented as length-counted byte strings of up to 255 characters length. 
  
Starting in Excel 2007:
  
- **FP12** &ndash; a two-dimensional floating-point array structure supporting all the rows and columns starting in Excel 2007. 
    
- **XLOPER12** &ndash; a multi-type data structure that can represent all the worksheet data types (including errors), integers, range references, XLM macro sheet flow control types, and an internal binary storage data type. 
    
   > [!NOTE]
   > Strings are represented as length-counted Unicode strings of up to 32,767 characters long. 
  
## Registration data type codes

XLL functions are registered using the C API function **xlfRegister**, which takes as its third argument a string of letters that encode the return and argument types. This string also contains the information that tells Excel whether the function is volatile, is thread-safe (starting in Excel 2007), is macro sheet equivalent, and whether it returns its result by modifying an argument in place.
  
The following table is reproduced and discussed in more detail in the [xlfRegister (Form 1)](xlfregister-form-1.md) topic. It is reproduced here in order to provide a context for the rest of this section. For example, a function that takes a length-counted Unicode string (starting in Excel 2007) could be described as taking a type C% argument. 
  
|Data type|Pass by value|Pass by ref (pointer)|Comments|
|:-----|:-----|:-----|:-----|
|Boolean  <br/> |A  <br/> |L  <br/> |short (0=false or 1=true)  <br/> |
|double  <br/> |B  <br/> |E  <br/> ||
|char \*  <br/> ||C, F  <br/> |Null-terminated ASCII byte string  <br/> |
|unsigned char \*  <br/> ||D, G  <br/> |Length -counted ASCII byte string  <br/> |
|unsigned short \*  (starting in Excel 2007)  <br/> ||C%, F%  <br/> |Null-terminated Unicode wide character string  <br/> |
|unsigned short \*  (starting in Excel 2007)  <br/> ||D%, G%  <br/> |Length-counted Unicode wide character string  <br/> |
|unsigned short [int]  <br/> |H  <br/> ||WORD  <br/> |
|[signed] short [int]  <br/> |I  <br/> |M  <br/> |16-bit  <br/> |
|[signed long] int  <br/> |J  <br/> |N  <br/> |32-bit  <br/> |
|Array  <br/> ||O  <br/> | Passed as three arguments by reference:  <br/>1. short int \*rows  <br/>2. short int \*columns  <br/>3. double \*array  <br/> |
|Array  <br/> (starting in Excel 2007)  <br/> ||O%  <br/> | Passed as three arguments by reference:  <br/>1. int \*rows  <br/>2. int \*columns  <br/>3. double \*array  <br/> |
|FP  <br/> ||K  <br/> |Floating-point array structure  <br/> |
|FP12  <br/> (starting in Excel 2007)  <br/> ||K%  <br/> |Large grid floating-point array structure  <br/> |
|XLOPER  <br/> ||P  <br/> |Variable-type worksheet values and arrays  <br/> |
|||R  <br/> |Values, arrays, and range references  <br/> |
|XLOPER12  <br/> (starting in Excel 2007)  <br/> ||Q  <br/> |Variable-type worksheet values and arrays  <br/> |
|||U  <br/> |Values, arrays, and range references  <br/> |
   
The types **C%**, **F%**, **D%**, **G%**, **K%**, **O%**, **Q**, and **U** were all new in Microsoft Office Excel 2007 and are not supported in earlier versions. The string types **F**, **F%**, **G**, and **G%** are used for arguments that are modified-in-place. When **XLOPER** or **XLOPER12** arguments are registered as types **P** or **Q** respectively, Excel converts single-cell references to simple values and multi-cell references to arrays when it prepares them. 
  
**P** and **Q** types always arrive in your function as one of the following types: **xltypeNum**, **xltypeStr**, **xltypeBool**, **xltypeErr**, **xltypeMulti**, **xltypeMissing**, or **xltypeNil**, but not **xltypeRef** or **xltypeSRef** because these are always dereferenced. 
  
Type **O**, which is really three arguments on the stack, was introduced for compatibility with Fortran DLLs where arguments are passed by reference. It cannot be used to return a value except by declaring the argument as a modify-in-place return value and placing the results in the referenced values. Type **O%** extends type **O** in Excel 2007 so that it can access arrays that cover areas larger than the Office Excel 2003 grid. 
  
## See also

- [xlfRegister (Form 1)](xlfregister-form-1.md)
- [Excel Programming Concepts](excel-programming-concepts.md)
- [Excel XLL SDK API Function Reference](excel-xll-sdk-api-function-reference.md)

