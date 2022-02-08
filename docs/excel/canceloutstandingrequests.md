---
title: "CancelOutstandingRequests"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 0de9d4e2-eb3f-40e7-aa24-f430892eb9ec

---

# CancelOutstandingRequests

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Informs the cluster connector that an Excel calculation has been canceled, and therefore all pending function calls within that session may be cancelled as well (and that Excel does not expect callbacks with their results).
  
```cpp
int CancelOutstandingRequests(int SessionId)
```

## Parameters

_SessionID_
  
> The ID of the session used by the canceled calculation. This value matches the value returned by [OpenSession](opensession.md).
    
## Return value

**xlHpcRetSuccess** if the _SessionId_ argument is valid; **xlHpcRetInvalidSessionId** if the _SessionId_ argument is invalid; **xlHpcRetCallFailed** on other failures. 
  
## Remarks

Implementers should stop all processes for the session for improved performance, as any results received after this call will be discarded by Excel.
  
## See also

- [Excel Cluster Connector Functions](excel-cluster-connector-functions.md)

