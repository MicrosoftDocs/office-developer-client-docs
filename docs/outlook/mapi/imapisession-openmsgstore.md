---
title: "IMAPISessionOpenMsgStore"
description: "Describes the syntax, parameters, and return value of IMAPISessionOpenMsgStore, which opens a message store and returns an IMsgStore pointer for further access."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISession.OpenMsgStore
api_type:
- COM
ms.assetid: 7f73b5cf-7093-42e9-8acc-63d73df77cf5
---

# IMAPISession::OpenMsgStore

**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens a message store and returns an [IMsgStore](imsgstoreimapiprop.md) pointer for further access. 
  
```cpp
HRESULT OpenMsgStore(
  ULONG_PTR ulUIParam,
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPCIID lpInterface,
  ULONG ulFlags,
  LPMDB FAR * lppMDB
);
```

## Parameters

_ulUIParam_
  
> [in] A handle to the parent window of the common address dialog box and other related displays.
    
_cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
_lpEntryID_
  
> [in] A pointer to the entry identifier of the message store to be opened. The  _lpEntryID_ parameter must not be NULL. 
    
_lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the message store. Passing NULL causes the  _lppMDB_ parameter to return a pointer to the standard interface for a message store (**IMsgStore**).
    
_ulFlags_
  
> [in] A bitmask of flags that controls how the object is opened. The following flags can be used:
    
  - MAPI_BEST_ACCESS: Requests that the message store be opened with the maximum network permissions allowed for the user and the maximum client application permissions. For example, if the client has read/write permission, the message store should be opened with read/write permission; if the client has read-only permission, the message store should be opened with read-only permission. 
      
  - MAPI_DEFERRED_ERRORS: Allows **OpenMsgStore** to return successfully, possibly before the message store is fully available to the calling client. If the message store is not available, making a subsequent object call can raise an error. 
      
  - MDB\_NO_DIALOG: Prevents the display of logon dialog boxes. If this flag is set, and **OpenMsgStore** has insufficient configuration information to open the message store without the user's help, it returns MAPI_E_LOGON_FAILED. If this flag is not set, the message store provider can prompt the user to correct a name or password or to perform other actions that are needed to establish a connection to the message store. 
      
  - MDB\_NO_MAIL: The message store should not be used for sending or receiving mail. When this flag is set, MAPI does not notify the MAPI spooler that this message store is being opened.
      
  - MDB\_ONLINE: In Cached Exchange Mode, a client or service provider can call this method with MDB_ONLINE to override the connection to the local message store and open the store on the remote server. You cannot open an Exchange store in cached mode and in non-cached mode at the same time in the same MAPI session. If you have already opened the cached message store, you must either close the store before you open it with this flag, or open a new MAPI session where you can open the Exchange store on the remote server by using this flag.
      
  - MDB_TEMPORARY: Instructs MAPI that the message store is not permanent and should not be added to the message store table. This flag is used to log on to the message store so information can be retrieved programmatically from the profile section. 
      
  - MDB_WRITE: Requests read/write permission to the message store.
    
_lppMDB_
  
> [out] Pointer to a pointer of the message store.
    
## Return value

S_OK 
  
> The message store was successfully opened.
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to access a message store for which the user has insufficient permissions.
    
MAPI_E_NOT_FOUND 
  
> The message store indicated by  _lpEntryID_ does not exist. 
    
MAPI_E_UNKNOWN_CPID 
  
> The server is not configured to support the client's code page.
    
MAPI_E_UNKNOWN_LCID 
  
> The server is not configured to support the client's locale information.
    
MAPI_W_ERRORS_RETURNED 
  
> The call succeeded, but the message store provider has error information available. When this warning is returned, the call should be handled as successful. To get the error information from the provider, call the [IMAPISession::GetLastError](imapisession-getlasterror.md) method. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPISession::OpenMsgStore** method opens a particular message store. 
  
## Notes to callers

The default permission level for message stores is read-only. If you set the MDB_WRITE flag, you still might not be granted read/write permission. The final level of access that MAPI assigns to the message store depends on your permission level, the message store itself, and the message store provider. 
  
If you call **OpenMsgStore** to open a message store with read-only permission, the following will occur: 
  
- The store's **PR\_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property will not have its STORE\_MODIFY_OK and STORE\_CREATE_OK bits set. 
    
- Calls to open one of the message store's messages or folders by using [IMAPISession::OpenEntry](imapisession-openentry.md) with the MAPI_MODIFY flag set will fail. 
    
- Calls to open one of the properties of the message store's messages or folders by using [IMAPIProp::OpenProperty](imapiprop-openproperty.md) with the MAPI_MODIFY flag will fail. 
    
- Calls to any of the following methods will fail: 
    
  - [IMAPIFolder::CreateMessage](imapifolder-createmessage.md)
    
  - [IMAPIFolder::DeleteMessages](imapifolder-deletemessages.md)
    
  - [IMAPIFolder::CreateFolder](imapifolder-createfolder.md)
    
  - [IMAPIFolder::DeleteFolder](imapifolder-deletefolder.md)
    
  - [IMAPIFolder::SetMessageStatus](imapifolder-setmessagestatus.md)
    
  - [IMAPIProp::SetProps](imapiprop-setprops.md)
    
  - [IMAPIProp::DeleteProps](imapiprop-deleteprops.md)
  
- Calls to the following methods will fail if the destination for the copied message is read-only, whether the destination is the same as the source message store or is another read-only store.
    
  - [IMAPIFolder::CopyMessages](imapifolder-copymessages.md)
    
  - [IMAPIFolder::CopyFolder](imapifolder-copyfolder.md)
    
  - [IMAPIProp::CopyTo](imapiprop-copyto.md)
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIStoreFunctions.cpp  <br/> |CallOpenMsgStore  <br/> |MFCMAPI uses the **IMAPISession::OpenMsgStore** method to open a message store. |
   
## See also

- [IMsgStore : IMAPIProp](imsgstoreimapiprop.md)
- [IMAPISession::GetLastError](imapisession-getlasterror.md)
- [IMAPISession::OpenEntry](imapisession-openentry.md)
- [IMAPIProp::OpenProperty](imapiprop-openproperty.md)
- [IMAPISession : IUnknown](imapisessioniunknown.md)
- [MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
- [Using Macros for Error Handling](using-macros-for-error-handling.md)

