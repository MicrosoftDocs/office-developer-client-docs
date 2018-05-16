---
title: "IMsgStoreAbortSubmit"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMsgStore.AbortSubmit
api_type:
- COM
ms.assetid: 9be6b88e-2510-4b82-8b35-5f20a0f99fc0
description: "Last modified: March 09, 2015"
---

# IMsgStore::AbortSubmit

  
  
**Applies to**: Outlook 
  
Attempts to remove a message from the outgoing queue.
  
```
AbortSubmit(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  ULONG ulFlags
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the message to remove from the outgoing queue. 
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
## Return value

S_OK 
  
> The message was successfully removed from the outgoing queue.
    
MAPI_E_NOT_IN_QUEUE 
  
> The message identified by  _lpEntryID_ is no longer in the message store's outgoing queue, typically because it has already been sent. 
    
MAPI_E_UNABLE_TO_ABORT 
  
> The message identified by  _lpEntryID_ is locked by the MAPI spooler, and the operation cannot be aborted. 
    
## Remarks

The **IMsgStore::AbortSubmit** method attempts to remove a submitted message from the message store's outgoing queue. 
  
## Notes to Callers

After a message is submitted, aborting the submission by calling **AbortSubmit** is the only action that can be performed on the message. Do not expect **AbortSubmit** to always succeed. Depending on how the underlying messaging system is implemented, it might not be possible to cancel the sending of the message. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FolderDlg.cpp  <br/> |CFolderDlg::OnAbortSubmit  <br/> |MFCMAPI uses the **IMsgStore::AbortSubmit** method to abort the submission of the selected message.  <br/> |
   
## See also

#### Reference

[IMessage::SubmitMessage](imessage-submitmessage.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

