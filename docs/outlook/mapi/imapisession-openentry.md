---
title: "IMAPISessionOpenEntry"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISession.OpenEntry
api_type:
- COM
ms.assetid: a4df4860-cf4f-4e97-97c4-fcd89b7f1f91
description: "Last modified: March 09, 2015"
---

# IMAPISession::OpenEntry

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Opens an object and returns an interface pointer for additional access.
  
```
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
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the object to open.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the opened object. Passing NULL returns the object's standard interface. For example, if the object to be opened is a message, the standard interface is [IMessage](imessageimapiprop.md); for folders, it is [IMAPIFolder](imapifolderimapicontainer.md). The standard interfaces for address book objects are [IDistList](idistlistimapicontainer.md) for a distribution list and [IMailUser](imailuserimapiprop.md) for a messaging user. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the object is opened. The following flags can be used:
    
MAPI_BEST_ACCESS 
  
> Requests that the object be opened by using the maximum network permissions allowed for the user and the maximum client application access. For example, if the client has read/write permission, the object should be opened with read/write permission; if the client has read-only permission, the object should be opened with read-only permission. 
    
MAPI_CACHE_OK
  
> Use all means, including offline address books, to perform name resolution.
    
MAPI_CACHE_ONLY
  
> Use only the offline address book to perform name resolution. For example, you can use this flag to allow a client application to open the global address list (GAL) in cached exchange mode and access an entry in that address book from the cache without creating traffic between the client and the server. This flag is supported only by the Exchange Address Book Provider.
    
MAPI_DEFERRED_ERRORS 
  
> Allows **OpenEntry** to return successfully, possibly before the object is fully available to the calling client. If the object is not available, making a subsequent object call can cause an error. 
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, objects are opened with read-only permission, and clients should not work on the assumption that read/write permission is granted. 
    
MAPI_NO_CACHE
  
> Do not use the offline address book to perform name resolution. This flag is supported only by the Exchange Address Book Provider.
    
SHOW_SOFT_DELETES
  
> Show items that are currently marked as soft deleted (that is, they are in the deleted item retention time phase).
    
 _lpulObjType_
  
> [out] A pointer to the type of the opened object.
    
 _lppUnk_
  
> [out] A pointer to a pointer to the opened object.
    
## Return value

S_OK 
  
> The object was opened successfully.
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to modify a read-only object or an attempt was made to access an object for which the user has insufficient permissions.
    
MAPI_E_NOT_FOUND 
  
> There is not an object associated with the entry identifier passed in the  _lpEntryID_ parameter. 
    
MAPI_E_UNKNOWN_ENTRYID 
  
> The entry identifier passed in the  _lpEntryID_ parameter is in an unrecognizable format. This value is typically returned if the service provider that contains the object is not open. 
    
## Remarks

The **IMAPISession::OpenEntry** method opens a message store or address book object, returning a pointer to an interface that can be used to access the object. 
  
## Notes to Callers

> [!IMPORTANT]
> When opening folder entries on a public store, such as folders and messages, use [IMsgStore::OpenEntry](imsgstore-openentry.md) instead of **IMAPISession::OpenEntry**. This ensures that public folders function correctly when multiple Exchange accounts are defined in a profile. 
  
Call **IMAPISession::OpenEntry** only when you do not know what kind of object that you are opening. If you know that you are opening a folder or a message, call [IMsgStore::OpenEntry](imsgstore-openentry.md). If you know that you are opening an address book container, a messaging user, or a distribution list, call [IAddrBook::OpenEntry](iaddrbook-openentry.md). These more specific methods are faster than **IMAPISession::OpenEntry**. 
  
MAPI opens all objects with read-only permission, unless you set the MAPI_MODIFY or MAPI_BEST_ACCESS flag in the  _ulFlags_ parameter. Setting one of these flags does not guarantee a particular type of access; the permissions that are granted depend on the service provider, the access level, and the object. To determine the access level of the opened object, retrieve its **PR_ACCESS_LEVEL** ( [PidTagAccessLevel](pidtagaccesslevel-canonical-property.md)) property.
  
Calling **IMAPISession::OpenEntry** and setting  _lpEntryID_ to point to the entry identifier of a message store is the same as calling the [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md) method with the MDB_NO_DIALOG flag set. The flag settings are also equivalent, except that to request read/write permission with **OpenMsgStore**, you must set the MDB_WRITE flag instead of MAPI_MODIFY. 
  
Check the value returned in the  _lpulObjType_ parameter to determine whether the object type returned is what you expected. If the object type is not the type that you expected, cast the pointer from the  _lppUnk_ parameter to a pointer of the appropriate type. For example, if you are opening a folder, cast  _lppUnk_ to a pointer of type LPMAPIFOLDER. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFunctions.cpp  <br/> |CallOpenEntry  <br/> |MFCMAPI uses the **IMAPISession::OpenEntry** method to open an object.  <br/> |
   
## See also

#### Reference

[IAddrBook::OpenEntry](iaddrbook-openentry.md)
  
[IDistList : IMAPIContainer](idistlistimapicontainer.md)
  
[IMailUser : IMAPIProp](imailuserimapiprop.md)
  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)
  
[IMAPISession::OpenMsgStore](imapisession-openmsgstore.md)
  
[IMessage : IMAPIProp](imessageimapiprop.md)
  
[IMsgStore::OpenEntry](imsgstore-openentry.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

