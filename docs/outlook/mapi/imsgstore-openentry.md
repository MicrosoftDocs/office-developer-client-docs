---
title: "IMsgStoreOpenEntry"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgStore.OpenEntry
api_type:
- COM
ms.assetid: a63c42cf-36af-466b-b41e-d6b53ce1c9fb
description: "Last modified: March 09, 2015"
---

# IMsgStore::OpenEntry

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens a folder or message and returns an interface pointer for further access. 
  
```cpp
HRESULT OpenEntry(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPCIID lpInterface,
  ULONG ulFlags,
  ULONG FAR * lpulObjType,
  LPUNKNOWN FAR * lppUnk
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter  _._
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the object to open, or NULL. If  _lpEntryID_ is set to NULL, **OpenEntry** opens the root folder for the message store. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the opened object. Passing NULL results in the object's standard interface ([IMAPIFolder](imapifolderimapicontainer.md) for folders and [IMessage](imessageimapiprop.md) for messages) being returned. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the object is opened. The following flags can be used:
    
MAPI_BEST_ACCESS 
  
> Requests that the object be opened by using the maximum network permissions allowed for the user and the maximum client application access. For example, if the client has read/write permission, the object should be opened by using read/write permission; if the client has read-only permission, the object should be opened by using read-only permission. 
    
MAPI_DEFERRED_ERRORS 
  
> Allows **OpenEntry** to return successfully, possibly before the object is fully available to the calling client. If the object is not available, making a subsequent object call can raise an error. 
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, objects are opened with read-only permission, and clients should not work on the assumption that read/write permission is granted. 
    
 _lpulObjType_
  
> [out] A pointer to the type of the opened object.
    
 _lppUnk_
  
> [out] A pointer to a pointer to the opened object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to modify a read-only object or to access an object for which the user has insufficient permissions.
    
MAPI_NO_CACHE
  
> When a store is opened in cached mode, a client or service provider can call **IMsgStore::OpenEntry**, setting the MAPI_NO_CACHE flag to open an item or a folder on the remote store. If you open the message store with the MDB_ONLINE flag on the remote server, you do not have to use the MAPI_NO_CACHE flag.
    
## Remarks

The **IMsgStore::OpenEntry** method opens a folder or message and returns a pointer to an interface that can be used for further access. 
  
> [!IMPORTANT]
> When opening folder entries on a public store, such as folders and messages, use **IMsgStore::OpenEntry** instead of [IMAPISession::OpenEntry](imapisession-openentry.md). This ensures that public folders function correctly when multiple Exchange accounts are defined in a profile. 
  
## Notes to callers

Folders and messages are automatically opened with read-only permission, unless you set the MAPI_MODIFY or MAPI_BEST_ACCESS flag in the  _ulFlags_ parameter. Setting one of these flags does not guarantee a particular type of permission; the permissions that you are granted depend on the message store provider, your access level, and the object. To determine the access level of the opened object, retrieve its **PR_ACCESS_LEVEL** ([PidTagAccessLevel](pidtagaccesslevel-canonical-property.md)) property.
  
Although **IMsgStore::OpenEntry** can be used to open any folder or message, it is usually faster to use the [IMAPIContainer::OpenEntry](imapicontainer-openentry.md) method if you have access to the parent folder of the folder or message to be opened. 
  
Check the value returned in the  _lpulObjType_ parameter to determine whether the returned object type is what you expected. If the object type is not the expected type, cast the pointer from the  _lppUnk_ parameter to a pointer of the appropriate type. For example, if you are opening a folder, cast  _lppUnk_ to a pointer of type **LPMAPIFOLDER**.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFunctions.cpp  <br/> |CallOpenEntry  <br/> |MFCMAPI uses the **IMsgStore::OpenEntry** method to open the object associated with an entry ID.  <br/> |
   
## See also



[IMAPIContainer::OpenEntry](imapicontainer-openentry.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

