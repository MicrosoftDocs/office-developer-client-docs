---
title: "IABProviderShutdown"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IABProvider.Shutdown
api_type:
- COM
ms.assetid: 1fbe6dc1-254b-4557-92c8-9fa42a8efd64
description: "Last modified: July 23, 2011"
---

# IABProvider::Shutdown

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Cancels a connection to an active session.
  
```
HRESULT Shutdown(
  ULONG FAR * lpulFlags
);
```

## Parameters

 _lpulFlags_
  
> [In] Reserved; must be a pointer to zero.
    
## Return value

S_OK 
  
> The connection was successfully canceled.
    
## Notes to Implementers

In your implementation of the **Shutdown** method, perform whatever tasks you consider necessary. MAPI calls your **Shutdown** method only after you have released all your logon objects. 
  
## See also

#### Reference

[IABProvider : IUnknown](iabprovideriunknown.md)

