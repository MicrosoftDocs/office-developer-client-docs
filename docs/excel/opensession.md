---
title: "OpenSession"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 6cfd3513-800f-4602-b3e6-6430920718d6

---

# OpenSession

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Creates a session in which user-defined functions can be executed.
  
```cpp
int OpenSession(WCHAR *Params)
```

## Parameters

_Params_
  
> A pointer to semicolon-delimited UNICODE string of parameters for the session. Excel does not use this argument.
    
## Return value

A session ID to use in other calls to the cluster connector, if the session was successfully created; otherwise **xlHpcRetCallFailed**.
  
## See also

- [Excel Cluster Connector Functions](excel-cluster-connector-functions.md)

