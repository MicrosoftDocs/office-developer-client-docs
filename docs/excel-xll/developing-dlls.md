---
title: "Developing DLLs"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- dlls [excel 2007], creating,creating DLLs [Excel 2007]
 
localization_priority: Normal
ms.assetid: 5d69d06d-a126-4c47-82ad-17112674c8a3
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Developing DLLs

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
A library is a body of compiled code that provides some functionality and data to an executable application. Libraries can be either statically linked or dynamically linked, and they conventionally have the file name extensions .lib and .dll respectively. Static libraries (such as the C run-time library) are linked to the application at compilation and so become part of the resulting executable. The application loads a DLL when it is needed, usually when the application starts up. One DLL can load and dynamically link to another DLL.
  
## Benefits of Using DLLs

The main benefits of DLLs are as follows:
  
- All applications can share a single copy on disk.
    
- Applications' executable files are kept smaller.
    
- They enable large development projects to be broken down. Application and DLL developers only need agree an interface between their respective parts. This interface is exported by the DLL.
    
- DLL developers can update DLLs—perhaps to make them more efficient or to fix a bug—without having to update all the applications that use it, provided that the exported interface of the DLL does not change.
    
You can use DLLs to add worksheet functions and commands in Microsoft Excel.
  
## Resources for Creating DLLs

To create a DLL, you need the following:
  
- A source code editor.
    
- A compiler to turn source code into object code that is compatible with your hardware.
    
- A linker to add code from static libraries, where used, and to create the executable DLL file.
    
Modern integrated development environments (IDEs), such as Microsoft Visual Studio, provide all of these things. They also provide a great deal more: smart editors, tools to debug your code, tools to manage multiple projects, new project wizards, and many other important tools.
  
You can create DLLs in several languages, for example, C/C++, Pascal and Visual Basic. Given that the API source code provided with Excel is C and C++, only these two languages are considered in this documentation.
  
## Exporting Functions and Commands

When compiling a DLL project, the compiler and linker need to know what functions are to be exported so that they can make them available to the application. This section describes the ways this can be done.
  
When compilers compile source code, in general, they change the names of the functions from their appearance in the source code. They usually do this by adding to the beginning and/or end of the name, in a process known as name decoration. You need to make sure that the function is exported with a name that is recognizable to the application loading the DLL. This can mean telling the linker to associate the decorated name with a simpler export name. The export name can be the name as it originally appeared in the source code, or something else.
  
The way the name is decorated depends on the language and how the compiler is instructed to make the function available, that is, the calling convention. The standard inter-process calling convention for Windows used by DLLs is known as the WinAPI convention. It is defined in Windows header files as **WINAPI**, which is in turn defined using the Win32 declarator **__stdcall**.
  
A DLL-export function for use with Excel (whether it is a worksheet function, macro-sheet equivalent function, or user-defined command) should always use the **WINAPI** / **__stdcall** calling convention. It is necessary to include the **WINAPI** specifier explicitly in the function's definition as the default in Win32 compilers is to use the **__cdecl** calling convention, also defined as **WINAPIV**, if none is specified.
  
You can tell the linker that a function is to be exported, and the name it is to be known by externally in one of several ways:
  
- Place the function in a DEF file after the **EXPORTS** keyword, and set your DLL project setting to reference this file when linking. 
    
- Use the **__declspec(dllexport)** declarator in the function's definition. 
    
- Use a **#pragma** preprocessor directive to send a message to the linker. 
    
Although your project can use all three methods and your compiler and linker support them, you should not try to export one function in more than one of these ways. For example, suppose that a DLL contains two source code modules, one C and one C++, which contain two functions to be exported, **my_C_export** and **my_Cpp_export** respectively. For simplicity, suppose that each function takes a single double-precision numerical argument and returns the same data type. The alternatives for exporting each function using each of these methods are outlined in the following sections. 
  
### Using a DEF File

```
double WINAPI my_C_export(double x)
{
/* Modify x and return it. */
    return x * 2.0;
}
```

```cs
double WINAPI my_Cpp_export(double x)
{
// Modify x and return it.
    return x * 2.0;
}
```

The DEF file would then need to contain these lines.
  
```
EXPORTS
    my_C_export = _my_C_export@8
    my_Cpp_export
```

The general syntax of a line that follows an **EXPORTS** statement is as follows. 
  
```
entryname[=internalname] [@ordinal[NONAME]] [DATA] [PRIVATE]

```

Note that the C function has been decorated, but the DEF file explicitly forces the linker to expose the function using the original source code name (in this example). The linker implicitly exports the C++ function using the original code name, so that it is not necessary to include the decorated name in the DEF file.
  
For 32-bit Windows API function calls, the convention for the decoration of C-compiled functions is as follows: **function_name** becomes _ **function_name@** _n_ where  _n_ is the number of bytes expressed as a decimal taken up by all the arguments, with the bytes for each rounded up to the nearest multiple of four. 
  
> [!NOTE]
> All pointers are four bytes wide in Win32. The return type has no impact on name decoration. 
  
It is possible to force the C++ compiler to expose undecorated names for C++ functions by enclosing the function, and any function prototypes, within an extern "C" {…} block, as shown in this example. (The braces **{}** are omitted here because the declaration only refers to the function code block that immediately follows it). 
  
```cs
extern "C"
double WINAPI my_undecorated_Cpp_export(double x)
{
// Modify x and return it.
    return x * 2.0;
}

```

When you are placing C function prototypes in header files that could be included in C or C++ source files, you should include the following pre-processor directive.
  
```cs
#ifdef __cplusplus
extern "C" {
#endif
double WINAPI my_C_export(double x);
double WINAPI my_Cdecorated_Cpp_export(double x);
#ifdef __cplusplus
}
#endif
```

### Using the __declspec(dllexport) Declarator

The **__declspec(dllexport)** keyword can be used in the declaration of the function as follows. 
  
```
__declspec(dllexport) double WINAPI my_C_export(double x)
{
/* Modify x and return it. */
    return x * 2.0;
}
```

The **__declspec(dllexport)** keyword must be added at the extreme left of the declaration. The advantages of this approach are that the function does not need to be listed in a DEF file, and that the export status is right with the definition. 
  
If you want to avoid a C++ function being made available with the C++ name decoration, you must declare the function as follows.
  
```cs
extern "C"
__declspec(dllexport) double WINAPI my_undecorated_Cpp_export(double x)
{
// Modify x and return it.
    return x * 2.0;
}
```

The linker will make the function available as my_undecorated_Cpp_export, that is, the name as it appears in the source code with no decoration.
  
### Using a #pragma Preprocessor Linker Directive

Recent versions of Microsoft Visual Studio support two predefined macros that, when used in conjunction with a **#pragma** directive, enable you to instruct the linker to export the function directly from within the function code. The macros are __FUNCTION__ and __FUNCDNAME__ (note the double underline at each end) which are expanded to the undecorated and decorated function names respectively. 
  
For example, when you are using Microsoft Visual Studio, these lines can be incorporated into a common header file as follows.
  
```cs
#if _MSC_VER > 1200 // Later than Visual Studio 6.0
#define EXPORT comment(linker, "/EXPORT:"__FUNCTION__"="__FUNCDNAME__)
#else // Cannot use this way of exporting functions.
#define EXPORT
#endif // else need to use DEF file or __declspec(dllexport)

```

If this header is included in the source files, the two example functions can then be exported as follows.
  
C code:
  
```
double WINAPI my_C_export(double x)
{
#pragma EXPORT
/* Modify x and return it. */
    return x * 2.0;
}
```

C++ code:
  
```cs
double WINAPI my_Cpp_export(double x)
{
#pragma EXPORT
// Modify x and return it.
    return x * 2.0;
}
```

Note that the directive must be placed within the body of the function and is only expanded when neither of the compiler options **/EP** or **/P** is set. This technique removes the need for a DEF file, or **__declspec(dllexport)** declaration, and keeps the specification of its export status with the function code. 
  
## See also

#### Concepts

[Access DLLs in Excel](how-to-access-dlls-in-excel.md)
  
[Calling into Excel from the DLL or XLL](calling-into-excel-from-the-dll-or-xll.md)
  
[Excel Programming Concepts](excel-programming-concepts.md)
  
[Developing Excel XLLs](developing-excel-xlls.md)

