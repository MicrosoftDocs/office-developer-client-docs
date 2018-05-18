---
title: "xlRunningOnCluster"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
keywords:
- xlrunningoncluster
 
localization_priority: Normal
ms.assetid: 7662f255-4184-4af0-97f5-9a89347a201a
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlRunningOnCluster

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Returns a value that indicates whether the user-defined function is running on a cluster. 
  
```
Excel12(xlRunningOnCluster, LPXLOPER12 pxRes, 0);
```

## Parameters

This function has no arguments.
  
## Return value

If the function is running in an Excel process, returns 0 in an **XLOPER12** of type **xlTypeInt**. If the function is running on a cluster, the return type and value is determined by the cluster connector provider.
  
## Requirements

This function is defined in the Xlcall.h header file.
  
## See also



[Cluster Safe Functions](cluster-safe-functions.md)
  
[C API Functions That Can Be Called Only from a DLL or XLL](c-api-functions-that-can-be-called-only-from-a-dll-or-xll.md)

