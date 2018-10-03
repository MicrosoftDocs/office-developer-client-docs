---
title: "Backward compatibility"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- version compatibility [excel 2007],XLL compatibility [Excel 2007],backward compatibility [Excel 2007]
localization_priority: Normal
ms.assetid: ac200824-0620-4f03-8bd2-59226c1e79d7
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Backward compatibility

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
This topic addresses issues of XLL compatibility in different versions of Microsoft Excel.
  
## Useful constant definitions

Consider including definitions similar to these in your XLL project code and replacing all instances of literal numbers used in this context. This will clarify code that is version specific, and reduce the likelihood of version-related bugs in the form of innocuous-looking numbers.
  
```cpp
#define MAX_XL11_ROWS            65536
#define MAX_XL11_COLS              256
#define MAX_XL12_ROWS          1048576
#define MAX_XL12_COLS            16384
#define MAX_XL11_UDF_ARGS           30
#define MAX_XL12_UDF_ARGS          255
#define MAX_XL4_STR_LEN           255u
#define MAX_XL12_STR_LEN        32767u
```

## Getting the running version

You should detect which version is running using  `Excel4(xlfGetWorkspace, &amp;version, 1, &amp;arg)`, where  `arg` is a numeric **XLOPER** set to 2 and version is a string **XLOPER** which can then be coerced to an integer. For Microsoft Excel 2013, this is 15.0. You should do this in, or from, the [xlAutoOpen](xlautoopen.md) function. You can then set a global variable that informs all of the modules in your project which version of Excel is running. Your code can then decide whether to call the C API using **Excel12** and **XLOPER12**s, or using **Excel4** using **XLOPER**s.
  
You can call **XLCallVer** to discover the C API version, but this does not indicate which of the pre-Excel 2007 versions you are running. 
  
## Creating add-ins that export dual interfaces

Consider an XLL function that takes a string and returns a value that can be any of the worksheet data types. You could export a function registered as type "PD" and prototyped as follows where the string is passed as a length-counted byte string.
  
`LPXLOPER WINAPI my_xll_fn(unsigned char *arg);`
  
Although this works perfectly well, there are several reasons why this is not the ideal interface to your code starting in Excel 2007:
  
- It is subject to the limitations of C API byte strings and cannot access the long Unicode strings supported starting in Excel 2007.
    
- Although, starting in Excel 2007, Excel can pass and accept **XLOPER**s, internally it converts them to **XLOPER12**s, so there is an implicit conversion overhead starting in Excel 2007 that is not there when the code runs in earlier versions of Excel.
    
- It may be that this function can be made thread safe, but if the type string is changed to  `PD$`, registration fails in starting before Excel 2007.
    
For these reasons, ideally, starting in Excel 2007 you should export a function for your users that was registered as  `QD%$`, assuming your code is thread safe and prototyped as follows.
  
`LPXLOPER12 WINAPI my_xll_fn_v12(wchar_t *arg);`
  
Another reason why you might want to register a different function starting in Excel 2007 is that it permits XLL functions to take up to 255 arguments, instead of the 30 limit of earlier versions.
  
Fortunately, you can have the benefits of both by exporting both versions from your project. You can then detect the running Excel version and conditionally register the most appropriate function. For more information and an example implementation, see [Developing Add-ins (XLLs) in Excel 2007](https://msdn.microsoft.com/library/aa730920.aspx).
  
This approach leads to the possibility that a worksheet running in Excel 2003 could display different results than the same sheet running starting in Excel 2007. For example, Excel 2003 would map a Unicode string in an Excel 2003 worksheet cell to an ASCII byte-string and truncate it before passing it to an XLL function. Starting in Excel 2007, Excel will pass an unconverted Unicode string to an XLL function registered in the right way. This could lead to a different result. You should be aware of this possibility and the consequences to your users, not just in the upgrade. For example, some built-in numeric functions were improved between Excel 2000 and Excel 2003.
  
## New Worksheet functions and Analysis Toolpak functions

Analysis Toolpak (ATP) functions are part of Excel starting in Excel 2007. Previously, an XLL could only call an ATP function by using [xlUDF](xludf.md). Starting in Excel 2007, the ATP functions should be called using the function enumerations defined in xlcall.h. The example in Calling User-defined Functions from DLLs demonstrates the two different methods.
  
## See also

- [C API Callback Functions Excel4, Excel12](c-api-callback-functions-excel4-excel12.md) 
- [Programming with the C API in Excel](programming-with-the-c-api-in-excel.md)
- [What's New in the C API for Excel](what-s-new-in-the-c-api-for-excel.md)

