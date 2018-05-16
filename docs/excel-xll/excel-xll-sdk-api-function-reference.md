---
title: "Excel XLL SDK API Function Reference"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- api function reference [excel 2007],functions [Excel 2007],reference [Excel 2007],Excel 2007 XLL Software Development Kit, reference
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 2f6df879-7546-4ac0-a4e3-6b009aee9463
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Excel XLL SDK API Function Reference

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
The Microsoft Excel 2013 XLL SDK contains source files for a Framework library that is designed to speed up the writing of XLLs, and two sample projects, Example and Generic. 
  
This section provides a function reference for the following:
  
- Excel callbacks that the XLL can call.
    
- XLL callbacks that Microsoft Excel looks for.
    
- Key functions in the sample and framework projects.
    
## Sample Projects

The Excel 2013 XLL SDK provides source files and Microsoft Visual Studio project files for the following sample projects:
  
- The **Framework** project (  `SAMPLES\FRAMEWRK\`) contains a project that can be built to a library, FRAMEWRK.lib, which can then be linked into other XLL projects. The library contains many functions and tools that make writing XLLs easier. This library is used in both of the other projects in conjunction with the header file FRAMEWRK.h.
    
- The **Example** project (  `SAMPLES\EXAMPLE\`) contains a project that can be built to an XLL, EXAMPLE.xll. The XLL contains many examples of the use of the Framework library, and example implementations of the XLL add-in interface functions such as **xlAutoOpen**.
    
- The **Generic** project (  `SAMPLES\GENERIC\`) contains a project that can be built to an XLL, GENERIC.xll. The XLL demonstrates several example functions and commands and is a good starting point for writing your own XLLs.
    
## In This Section

[Add-in Manager and XLL Interface Functions](add-in-manager-and-xll-interface-functions.md)
  
[C API Callback Functions Excel4, Excel12](c-api-callback-functions-excel4-excel12.md)
  
[Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)
  
[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)
  
[Functions in the Framework Library](functions-in-the-framework-library.md)
  
[Functions in the Generic DLL](functions-in-the-generic-dll.md)
  
[Excel Cluster Connector Functions](excel-cluster-connector-functions.md)
  
## See also

#### Concepts

[Programming with the C API in Excel](programming-with-the-c-api-in-excel.md)
  
[Developing Excel XLLs](developing-excel-xlls.md)

