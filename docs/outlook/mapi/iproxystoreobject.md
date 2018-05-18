---
title: "IProxyStoreObject"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProxyStoreObject
api_type:
- COM
ms.assetid: 567bede4-39a3-bfb4-af85-ba678e2cf4a5
description: "Last modified: March 09, 2015"
---

# IProxyStoreObject

  
  
**Applies to**: Outlook 
  
Provides an Internet Message Access Protocol (IMAP) store object that has been unwrapped and that allows access to items in the Personal Folders file (PST) without invoking synchronization and downloading the items.
  
## Quick info

|||
|:-----|:-----|
|Inherited from:  <br/> |[IUnknown](http://msdn.microsoft.com/en-us/library/ms680509%28v=VS.85%29.aspx) <br/> |
|Provided By:  <br/> |Message store provider  <br/> |
|Interface identifier:  <br/> |**IID_IProxyStoreObject** <br/> |
   
## Vtable order

|||
|:-----|:-----|
| *Placeholder member*  <br/> | *Not supported or documented.*  <br/> |
|[IProxyStoreObject::UnwrapNoRef](iproxystoreobject-unwrapnoref.md) <br/> |Gets a pointer to an unwrapped IMAP store.  <br/> |
| *Placeholder member*  <br/> | *Not supported or documented.*  <br/> |
   
## Remarks

Call [IUnknown::QueryInterface](http://msdn.microsoft.com/en-us/library/ms682521%28v=VS.85%29.aspx) on the source message store to obtain the **IProxyStoreObject** interface. Then call **IProxyStoreObject::UnwrapNoRef** to obtain the unwrapped store object. If **QueryInterface** returns the error **MAPI_E_INTERFACE_NOT_SUPPORTED**, then the store has not been wrapped. 
  
Because **UnwrapNoRef** does not increment the reference count for this new pointer to the unwrapped store object, after successfully calling **UnwrapNoRef**, you should call [IUnknown::AddRef](http://msdn.microsoft.com/en-us/library/ms691379%28v=VS.85%29.aspx) to maintain the reference count. 
  

