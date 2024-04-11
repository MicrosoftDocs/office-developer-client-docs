---
title: "Developing Excel XLLs"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- add-ins - [excel 2007],developing XLLs - [Excel 2007],XLLs - [Excel 2007], developing
ms.assetid: dd27ae4d-ef97-47db-885c-ddd955816900

ms.localizationpriority: high
---

# Developing Excel XLLs

**Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
The primary reason for writing Microsoft Excel XLLs and using the C API is to create high-performance worksheet functions. The applications of high-performance functions—and, starting in Excel 2007, the ability to write multithreaded interfaces to powerful server resources—make it a very important part of Excel extensibility. The performance of XLLs was further enhanced in Excel 2007 by the addition of new data types and, most important, support for multithreading.
  
The C API has none of the higher-level rapid development features of Microsoft Visual Basic for Applications (VBA), COM, or the Microsoft .NET Framework. Memory management is low level, and therefore puts greater responsibility on the developer. Many Excel features that are exposed through COM, making them available through VBA and the .NET Framework, are not exposed to the C API.

- [Excel Programming Concepts](excel-programming-concepts.md)
  
- [Working with DLLs](working-with-dlls.md)
  
- [Accessing XLL Code in Excel](accessing-xll-code-in-excel.md)
  
- [Call XLL Functions from the Function Wizard or Replace Dialog Boxes](how-to-call-xll-functions-from-the-function-wizard-or-replace-dialog-boxes.md)
  
- [Calling into Excel from the DLL or XLL](calling-into-excel-from-the-dll-or-xll.md)
  
- [Creating XLLs](creating-xlls.md)
  
- [Evaluating Names and Other Worksheet Formula Expressions](evaluating-names-and-other-worksheet-formula-expressions.md)
  
- [Multithreading and Memory Management](multithreading-and-memory-management.md)
  
- [Asynchronous User-Defined Functions](asynchronous-user-defined-functions.md)
  
- [Cluster Safe Functions](cluster-safe-functions.md)
  
- [Permitting User Breaks in Lengthy Operations](permitting-user-breaks-in-lengthy-operations.md)
  
- [Displaying Dialog Boxes from Within a DLL or XLL](displaying-dialog-boxes-from-within-a-dll-or-xll.md)
  
- [Access Excel Instance and Main Window Handles](how-to-access-excel-instance-and-main-window-handles.md)
  
- [Backward Compatibility](backward-compatibility.md)
  