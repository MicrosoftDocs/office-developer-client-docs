---
title: "C API Callback Functions Excel4, Excel12"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
keywords:
- functions [excel 2007], c api callback
 
localization_priority: Normal
ms.assetid: 0f3ae86d-329a-4177-a65b-6288c248297e
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# C API Callback Functions Excel4, Excel12

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
The **Excel4** and **Excel12** functions are provided to enable DLLs to call an internal Microsoft Excel worksheet function, macro sheet function or command, or XLL-only special function or command. All recent versions of Excel support the **Excel4** function. Starting in Excel 2007 the **Excel12** function is supported. Both functions are provided in two forms: 
  
- A variable-length argument list form ( **Excel4/Excel12**)
    
- An array-of-arguments form ( **Excel4v/Excel12v**)
    
Except for the way in which arguments are passed to these callbacks, the two forms are functionally equivalent. The basic concepts for both forms are fully described in [Excel4/Excel12](excel4-excel12.md). [Excel4v/Excel12v](excel4v-excel12v.md) covers other issues about this form. 
  
## In This Section

[Excel4/Excel12](excel4-excel12.md)
  
[Excel4v/Excel12v](excel4v-excel12v.md)
  

