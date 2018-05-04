---
title: "PingSession"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 4646659b-f932-4d11-a46f-4231bb397243
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# PingSession

 * **Applies to:** Excel 2013 | Office 2013 | Visual Studio * 
  
Checks whether a session is valid. This function is typically called when Excel needs to determine if a previously returned session ID is still active and can be used.
  
```
int PingSession(int SessionId)
```

## Parameters

 _SessionID_
  
> The ID of the session to ping. This value must match an ID returned by a previous call to [OpenSession](opensession.md).
    
## Return Value

 **xlHpcRetSuccess** if the  _SessionId_ argument is valid; otherwise **xlHpcRetInvalidSessionId**.
  
## See also

#### Reference

[OpenSession](opensession.md)
#### Concepts

[Excel Cluster Connector Functions](excel-cluster-connector-functions.md)

