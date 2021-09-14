---
title: "IProxyStoreObjectUnwrapNoRef"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IProxyStoreObject.UnwrapNoRef
api_type:
- COM
ms.assetid: 1122b6e0-e7e1-e68a-e090-435777343d04
description: "Last modified: July 23, 2011"
---

# IProxyStoreObject::UnwrapNoRef

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Gets a pointer to an unwrapped Internet Message Access Protocol (IMAP) store object that provides access to the underlying Personal Folders file (PST) without invoking synchronization and downloading the items.
  
```cpp
HRESULT IProxyStoreObject::UnwrapNoRef (     LPVOID *ppvObject ); 
```

## Parameters

 _ppvObject_
  
> [out] Pointer to an [IMsgStore : IMAPIProp](imsgstoreimapiprop.md) store object that is unwrapped. 
    
## Return values

S_OK
  
- The call was successful and a pointer to an unwrapped interface has been returned in  _ppvObject_.
    
## Remarks

Without first unwrapping an IMAP store, accessing a message in the store can force a synchronization that attempts to download the entire message. Using the unwrapped store allows access to the message in its current state without triggering a download.
  
Because **UnwrapNoRef** does not increment the reference count for this new pointer to the unwrapped store object, after successfully calling **UnwrapNoRef**, you should call [IUnknown::AddRef](https://msdn.microsoft.com/library/ms691379%28v=VS.85%29.aspx) to maintain the reference count. 
  
## See also



[IProxyStoreObject](iproxystoreobject.md)

