---
title: "OpenSession"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 6cfd3513-800f-4602-b3e6-6430920718d6
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# OpenSession

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Creates a session in which user-defined functions can be executed.
  
```
int OpenSession(WCHAR *Params)
```

## Parameters

 _Params_
  
> A pointer to semicolon-delimited UNICODE string of parameters for the session. Excel does not use this argument.
    
## Return Value

A session ID to use in other calls to the cluster connector, if the session was successfully created; otherwise **xlHpcRetCallFailed**.
  
## See also

#### Concepts

[Excel Cluster Connector Functions](excel-cluster-connector-functions.md)

