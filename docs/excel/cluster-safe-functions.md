---
title: "Cluster safe functions"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 787badaf-8782-454d-a016-7eae83bbd8a9

---

# Cluster safe functions

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
In Excel 2013, Excel can offload User-Defined Function (UDF) calls to a high-performance computing cluster through a dedicated cluster connector interface. Compute cluster vendors provide Cluster Connectors. UDF authors can declare their UDFs as cluster safe and then, when a cluster connector is present, Excel sends calls to these UDFs to the cluster connector for offloading.
  
When Excel discovers a cluster-safe UDF during recalculation, it passes the name of the XLL that is currently running, the name of the cluster-safe UDF, and any parameters to the cluster connector. The connector runs the UDF call remotely and returns the results to Excel. Non-dependent calculation continues and when the cluster connector has finished running the UDF, it passes the results to Excel and dependent calculations continue. The mechanism for this asynchronous behavior mimics the mechanism used by asynchronous UDFs, except that the cluster connector manages the asynchronous aspects instead of the UDF author. Typically, a cluster connector implements an XLL shim to load XLLs and run UDFs on compute cluster nodes.
  
The mechanics of declaring UDFs as cluster-safe resemble those of declaring UDFs as safe for multi-threaded recalculation. However, because the UDF is not necessarily running on the same computer as other UDFs from the same Excel session, there are different considerations when writing cluster-safe UDFs.
  
To register a UDF as cluster-safe, you must call the [xlfRegister (Form 1)](xlfregister-form-1.md) callback function through the **Excel12** or **Excel12v** interface. For more information about these interfaces, see the [Excel4/Excel12](excel4-excel12.md) and [Excel4v/Excel12v](excel4v-excel12v.md). Registering a UDF as cluster-safe through the **Excel4** or **Excel4v** interface is not supported. 
  
If you register a function as cluster-safe, you must ensure that the function behaves in a cluster-safe way. Although the exact behavior of the cluster connector is implementation-specific, you should design your UDF to run on a distributed computer system and to have the following characteristics:
  
- A UDF should not rely on any memory state. For example, a UDF should not rely on an existing in-memory cache.
    
- A UDF should not perform Excel callbacks that the cluster connector provider does not support.
    
In addition to cluster-safe behavior, there are the following technical restrictions on cluster-safe UDFs:
  
1. No XLOPER arguments (types 'P', 'R').
    
2. No XLOPER12 arguments that support range references (type 'U').
    
3. Cannot be a macro sheet equivalent function ('#' and '&amp;' cannot be combined).
    
For UDFs with shorter execution times, the overhead of offloading may be larger than the time it takes the UDF to execute, negating many of the benefits of using this infrastructure.
  
> [!NOTE]
> You cannot declare a cluster-safe UDF as an asynchronous UDF. 
  
A UDF can determine whether it is being run using a cluster connector by calling the [xlRunningOnCluster](xlrunningoncluster.md) callback function. 
  

