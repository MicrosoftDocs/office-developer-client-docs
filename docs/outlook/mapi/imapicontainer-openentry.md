---
title: "IMAPIContainerOpenEntry"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIContainer.OpenEntry
api_type:
- COM
ms.assetid: 0c46c1fb-dd63-4ac5-960e-80f68e75d8f4
description: "Last modified: July 23, 2011"
---

# IMAPIContainer::OpenEntry

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens an object in the container, returning an interface pointer for further access.
  
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
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the object to open. If  _lpEntryID_ is set to NULL, the top-level container in the container's hierarchy is opened. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the object. Passing NULL results in the identifier for the object's standard interface being returned. For messages, the standard interface is [IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md); for folders, it is [IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md). The standard interfaces for address book objects are [IDistList : IMAPIContainer](idistlistimapicontainer.md) for a distribution list and [IMailUser : IMAPIProp](imailuserimapiprop.md) for a messaging user. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the object is opened. The following flags can be set:
    
MAPI_BEST_ACCESS 
  
> Requests that the object will be opened with the maximum network permissions allowed for the user and the maximum client application access. For example, if the client has read/write permission, the object should be opened with read/write permission; if the client has read-only access, the object should be opened with read-only access. 
    
MAPI_DEFERRED_ERRORS 
  
> Allows **OpenEntry** to return successfully, possibly before the object is fully available to the calling client. If the object is not available, making a subsequent object call can raise an error. 
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, objects are opened with read-only access, and clients should not work on the assumption that read/write permission has been granted. 
    
SHOW_SOFT_DELETES
  
> Shows items that are currently marked as soft deleted—that is, they are in the deleted item retention time phase.
    
 _lpulObjType_
  
> [out] A pointer to the opened object's type.
    
 _lppUnk_
  
> [out] A pointer to a pointer to the interface implementation to use to access the open object.
    
## Return value

S_OK 
  
> The object was successfully opened.
    
MAPI_E_NO_ACCESS 
  
> Either the user has insufficient permissions to open the object or an attempt was made to open a read-only object with read/write permission.
    
MAPI_E_NOT_FOUND 
  
> The entry identifier specified by  _lpEntryID_ does not represent an object. 
    
MAPI_E_UNKNOWN_ENTRYID 
  
> The entry identifier in the  _lpEntryID_ parameter is not of a format recognized by the container. 
    
## Remarks

The **IMAPIContainer::OpenEntry** method opens an object throughout a container and returns a pointer to an interface implementation to use for further access. 
  
## Notes to callers

Because service providers are not required to return an interface implementation of the type specified by the interface identifier in the  _lpInterface_ parameter, check the value pointed to by the  _lpulObjType_ parameter. If necessary, cast the pointer returned in  _lppUnk_ to a pointer of the appropriate type. 
  
By default, service providers open objects with read-only access unless you set either the MAPI_MODIFY or MAPI_BEST_ACCESS flag. When one of these flags is set, service providers attempt to return a modifiable object. However, do not assume that because you requested a modifiable object that the opened object has read/write permission. Either plan for the chance of a subsequent modification to fail or retrieve the object's **PR_ACCESS_LEVEL** property to determine the access level granted by **OpenEntry**.
  
## See also



[IMAPIContainer : IMAPIProp](imapicontainerimapiprop.md)

