---
title: "IMSLogonOpenEntry"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMSLogon.OpenEntry
api_type:
- COM
ms.assetid: 612cbab7-60cb-48bb-906e-18d9135e7a86
description: "Last modified: July 23, 2011"
---

# IMSLogon::OpenEntry

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens a folder or message object and returns a pointer to the object to provide further access. 
  
```cpp
HRESULT OpenEntry(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPCIID lpInterface,
  ULONG ulOpenFlags,
  ULONG FAR * lpulObjType,
  LPUNKNOWN FAR * lppUnk
);
```

## Parameters

 _cbEntryID_
  
> [in] The size, in bytes, of the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the address of the entry identifier of the folder or message object to open. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) for the object. Passing NULL indicates that the object is cast to the standard interface for such an object. The  _lpInterface_ parameter can also be set to an identifier for an appropriate interface for the object. 
    
 _ulOpenFlags_
  
> [in] A bitmask of flags that controls how the object is opened. The following flags can be set:
    
MAPI_BEST_ACCESS 
  
> The object should be opened with the maximum permissions allowed for the user and the maximum client application permissions. For example, if the client has read/write permission, the object is opened with read/write permission; if the client has read-only permission, the object is opened with read-only permission. The client can retrieve the permission level by getting the **PR_ACCESS_LEVEL** ([PidTagAccessLevel](pidtagaccesslevel-canonical-property.md)) property.
    
MAPI_DEFERRED_ERRORS 
  
> The call is allowed to succeed even if the underlying object is not available to the calling application. If the object is not available, a subsequent call to the object might return an error.
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, objects are created with read-only permission, and clients should not work on the assumption that read/write permission has been granted. 
    
 _lpulObjType_
  
> [out] A pointer to the type of the opened object.
    
 _lppUnk_
  
> [out] A pointer to the pointer to the opened object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

MAPI calls the **IMSLogon::OpenEntry** method to open a folder or a message in a message store. MAPI passes in the entry identifier of the object to open. The message store provider should return a pointer that enables further access to the object specified in the  _lppUnk_ parameter. 
  
Before MAPI calls **IMSLogon::OpenEntry**, it first determines that the given message or folder entry identifier matches one registered by this message store provider. For more information about how store providers register entry identifiers, see [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md).
  
 **IMSLogon::OpenEntry** is identical to the [IMsgStore::OpenEntry](imsgstore-openentry.md) method of the message store object, except that the client does not call **IMSLogon::OpenEntry**; MAPI calls **IMSLogon::OpenEntry** when it processes an **IMAPISession::OpenEntry** method. Objects opened by using **IMSLogon::OpenEntry** should be treated exactly the same as objects opened by using the message store object; in particular, objects opened by using this call should be invalidated when the message store object is released. 
  
## See also



[IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md)
  
[IMsgStore::OpenEntry](imsgstore-openentry.md)
  
[IMSLogon : IUnknown](imslogoniunknown.md)

