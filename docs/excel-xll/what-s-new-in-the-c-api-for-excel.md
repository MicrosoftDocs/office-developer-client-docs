---
title: "What's New in the C API for Excel"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- c api [excel 2007], what's new
 
localization_priority: Normal
ms.assetid: f11552e1-b8ea-4933-b6fc-c452b07eb59d
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# What's New in the C API for Excel

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
In conjunction with Microsoft Excel 2013, the Microsoft Excel 2013 XLL Software Development Kit (SDK) includes support for the following features.
  
- **New Functions**
    
    The Microsoft Excel 2013 XLL SDK supports calling back to all of the new worksheet functions in Excel 2013. For more information about calling Excel 2013 functions, see [Calling into Excel from the DLL or XLL](calling-into-excel-from-the-dll-or-xll.md).
    
- **Asynchronous User-defined Functions**
    
    Excel 2013 supports calling user-defined functions (UDF) asynchronously, which can improve performance by enabling several calculations to run at the same time. For more information about asynchronous UDFs, see [Asynchronous User-Defined Functions](asynchronous-user-defined-functions.md).
    
- **Cluster Connectors**
    
    Cluster connectors enable UDFs to run on high-performance compute clusters. For more information about creating cluster connectors, see [Developing Excel Cluster Connectors](developing-excel-cluster-connectors.md).
    
    > [!NOTE]
    > XLL add-ins that you intend to run on compute clusters must call only cluster-safe functions. For more information about the functions you can use, see [Excel XLL SDK API Function Reference](excel-xll-sdk-api-function-reference.md) and [Cluster Safe Functions](cluster-safe-functions.md). 
  
- **64-bit Support**
    
    You can now compile and link both 32-bit and 64-bit XLLs. For more information, see [Creating XLLs](creating-xlls.md).
    
## See also

#### Concepts

[Developing Excel XLLs](developing-excel-xlls.md)
  
[Programming with the C API in Excel](programming-with-the-c-api-in-excel.md)
  
[Multithreading and Memory Contention in Excel](multithreading-and-memory-contention-in-excel.md)
#### Other resources

[Getting Started with the Excel XLL SDK](getting-started-with-the-excel-xll-sdk.md)

