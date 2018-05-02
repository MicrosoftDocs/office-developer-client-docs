---
title: "IMAPISessionSetDefaultStore"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISession.SetDefaultStore
api_type:
- COM
ms.assetid: 456c207f-5d41-4d0c-94b6-0c58893a6bed
description: "Last modified: March 09, 2015"
---

# IMAPISession::SetDefaultStore

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Establishes a message store as the default message store for the session.
  
```
HRESULT SetDefaultStore(
  ULONG ulFlags,
  ULONG cbEntryID,
  LPENTRYID lpEntryID
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the setting of the default message store. These flags are mutually exclusive; only one of the following flags can be set:
    
MAPI_DEFAULT_STORE
  
> Establishes the message store as the session default. Updates the message store's status table row by setting the STATUS_DEFAULT_STORE flag in the **PR_RESOURCE_FLAGS** ( [PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) column.
    
MAPI_PRIMARY_STORE
  
> Establishes the message store as the store to be used at logon. If the message store is not the default store, clients should make it the default. Updates the message store's status table row by setting the STATUS_PRIMARY_STORE flag in the **PR_RESOURCE_FLAGS** column. 
    
MAPI_SECONDARY_STORE
  
> Establishes the message store as the store to be used at logon if the primary message store is not available. If a client cannot open the primary store, it should open the secondary store and set it as the default. Updates the message store's status table row by setting the STATUS_SECONDARY_STORE flag in the **PR_RESOURCE_FLAGS** column. 
    
MAPI_SIMPLE_STORE_PERMANENT
  
> Sets the STATUS_SIMPLE_STORE flag in the message store's **PR_RESOURCE_FLAGS** property in its status table row, message store table row, and in the session profile. 
    
MAPI_SIMPLE_STORE_TEMPORARY
  
> Sets the STATUS_SIMPLE_STORE flag in the message store's **PR_RESOURCE_FLAGS** property in its status table row and message store table row. The profile is not modified. 
    
 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the message store that is intended as the default. If a client passes NULL in  _lpEntryID_, no message store is selected as the default.
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

The **IMAPISession::SetDefaultStore** method establishes a message store as one of the following: 
  
- The default message store for the session.
    
- The primary message store for the session.
    
- The secondary message store for the session.
    
To establish a message store as the default, the message store must have the following flags set in its **PR_STORE_SUPPORT_MASK** ( [PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property:
  
- STORE_SUBMIT_OK
    
- STORE_CREATE_OK
    
- STORE_MODIFY_OK
    
## Notes to Callers

You can determine the default message store for the session by retrieving the status table and searching for the setting of the STATUS_DEFAULT_STORE flag in the **PR_RESOURCE_FLAGS** column. The row that has this setting represents the message store that is designated as the session default. 
  
When either the MAPI_DEFAULT_STORE or the MAPI_SIMPLE_STORE_PERMANENT flag is set, MAPI updates the profile, message store table, and status table. 
  
Whenever a change is made to the message store default setting, the following notifications are generated:
  
- An **fnevTableModified** event notification is issued for each affected row in both the message store and status table. 
    
- An internal notification is issued to the MAPI spooler. Operations already in progress are completed without change; new operations that involve the default message store, such as message downloading, are processed for the new default store.
    
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnSetDefaultStore  <br/> |MFCMAPI uses the **IMAPISession::SetDefaultStore** method to set the selected store as the default store.  <br/> |
   
## See also

#### Reference

[PidTagResourceFlags Canonical Property](pidtagresourceflags-canonical-property.md)
  
[PidTagStoreSupportMask Canonical Property](pidtagstoresupportmask-canonical-property.md)
  
[TABLE_NOTIFICATION](table_notification.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

