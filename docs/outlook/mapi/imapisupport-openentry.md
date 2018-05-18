---
title: "IMAPISupportOpenEntry"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.OpenEntry
api_type:
- COM
ms.assetid: 84662230-6a25-4403-b87e-871427a40c6e
description: "Last modified: July 23, 2011"
---

# IMAPISupport::OpenEntry

  
  
**Applies to**: Outlook 
  
Opens an object and returns an interface pointer for further access. 
  
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
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the object to open.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the object. Passing NULL results in the object's standard interface being returned. For example, if the object to be opened is a message, the standard interface is [IMessage](imessageimapiprop.md); for folders, it is [IMAPIFolder](imapifolderimapicontainer.md). The standard interfaces for address book objects are [IDistList](idistlistimapicontainer.md) for a distribution list and [IMailUser](imailuserimapiprop.md) for a messaging user. 
    
 _ulOpenFlags_
  
> [in] A bitmask of flags that controls how the object is opened. The following flags can be set:
    
MAPI_BEST_ACCESS 
  
> Requests that the object be opened with the maximum network permissions allowed for the caller. For example, if the caller has read/write permission, the object should be opened as read/write; if the caller has read-only permission, the object should be opened as read-only. 
    
MAPI_DEFERRED_ERRORS 
  
> Allows **OpenEntry** to return successfully, possibly before the object is fully accessible to the caller. If the object is not accessible, making a subsequent object call can result in an error. 
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, objects are opened as read-only, and callers should not work on the assumption that read/write permission has been granted. 
    
 _lpulObjType_
  
> [out] A pointer to the type of the opened object.
    
 _lppUnk_
  
> [out] A pointer to a pointer to the opened object.
    
## Return value

S_OK 
  
> The object was successfully opened.
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to modify a read-only object, or an attempt was made to access an object for which the user has insufficient permissions.
    
MAPI_E_NOT_FOUND 
  
> There is not an object associated with the entry identifier passed in the  _lpEntryID_ parameter. 
    
MAPI_E_UNKNOWN_ENTRYID 
  
> The entry identifier passed in the  _lpEntryID_ parameter is in an unrecognizable format. This value is typically returned if the address book provider that contains the object is not open. 
    
## Remarks

The **IMAPISupport::OpenEntry** method is implemented for all service provider support objects. Service providers call **IMAPISupport::OpenEntry** to retrieve a pointer to an interface that can be used to access a particular object. 
  
## Notes to callers

Call **IMAPISupport::OpenEntry** only when you do not know what kind of object you are opening. If you know you are opening a folder or a message, call [IMsgStore::OpenEntry](imsgstore-openentry.md) instead. If you know you are opening an address book container, a messaging user, or a distribution list, call [IAddrBook::OpenEntry](iaddrbook-openentry.md). These more specific methods are faster than **IMAPISupport::OpenEntry**. 
  
 **IMAPISupport::OpenEntry** opens all objects as read-only, unless you set the MAPI_MODIFY or MAPI_BEST_ACCESS flag in the  _ulFlags_ parameter and your permissions are sufficient. Setting one of these flags does not guarantee a particular type of access; the permissions that you are granted depend on your access level, the object, and the service provider that owns the object. To determine the access level of the opened object, retrieve its **PR_ACCESS_LEVEL** ([PidTagAccessLevel](pidtagaccesslevel-canonical-property.md)) property.
  
Check the value returned in the  _lpulObjType_ parameter to determine that the object type returned is what you expected. If the object type is as expected, cast the pointer from the  _lppUnk_ parameter to a pointer of the appropriate type. For example, if you are opening a folder, cast  _lppUnk_ to a pointer of type LPMAPIFOLDER. 
  
## See also



[IMAPISupport : IUnknown](imapisupportiunknown.md)

