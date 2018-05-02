---
title: "IXPProviderShutdown"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IXPProvider.Shutdown
api_type:
- COM
ms.assetid: e2d8a025-c2a3-4edb-b6e4-022e07e854dd
description: "Last modified: July 23, 2011"
---

# IXPProvider::Shutdown

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Closes down a transport provider in an orderly fashion.
  
```
HRESULT Shutdown (
  ULONG FAR * lpulFlags
);
```

## Parameters

 _lpulFlags_
  
> [in] Reserved; must be zero.
    
## Return value

S_OK 
  
> The call succeeded in shutting down the transport provider.
    
## Remarks

The MAPI spooler calls the **IXPProvider::Shutdown** method just prior to releasing a transport provider object. Before calling **Shutdown**, MAPI releases all logon objects for a provider.
  
## See also

#### Reference

[XPProviderInit](xpproviderinit.md)
  
[IXPProvider : IUnknown](ixpprovideriunknown.md)

