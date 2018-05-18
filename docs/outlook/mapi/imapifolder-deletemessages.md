---
title: "IMAPIFolderDeleteMessages"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFolder.DeleteMessages
api_type:
- COM
ms.assetid: 5a16e62b-9d33-41cd-af2b-9abd403b6f2e
description: "Last modified: March 09, 2015"
---

# IMAPIFolder::DeleteMessages

  
  
**Applies to**: Outlook 
  
Deletes one or more messages.
  
```cpp
HRESULT DeleteMessages(
  LPENTRYLIST lpMsgList,
  ULONG_PTR ulUIParam,
  LPMAPIPROGRESS lpProgress,
  ULONG ulFlags
);
```

## Parameters

 _lpMsgList_
  
> [in] A pointer to an [ENTRYLIST](entrylist.md) structure that contains the number of messages to delete and an array of [ENTRYID](entryid.md) structures that identify the messages. 
    
 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator. The  _ulUIParam_ parameter is ignored unless the MESSAGE_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _lpProgress_
  
> [in] A pointer to a progress object that displays a progress indicator. If NULL is passed in  _lpProgress_, the message store provider displays a progress indicator by using the MAPI progress object implementation. The  _lpProgress_ parameter is ignored unless the MESSAGE_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the messages are deleted. The following flags can be set:
    
DELETE_HARD_DELETE
  
> Permanently removes all messages, including soft-deleted ones.
    
MESSAGE_DIALOG 
  
> Displays a progress indicator as the operation proceeds.
    
## Return value

S_OK 
  
> The specified message or messages were successfully deleted.
    
MAPI_W_PARTIAL_COMPLETION 
  
> The call succeeded, but not all of the messages were successfully deleted. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPIFolder::DeleteMessages** method deletes messages from a folder. Messages that do not exist, that have been moved elsewhere, that are open with read/write permission, or that are currently submitted cannot be deleted. 
  
## Notes to implementers

When the delete operation involves more than one message, perform the operation as completely as possible for each folder, even if one or more of the messages cannot be deleted. Do not stop the operation prematurely unless a failure occurs that is beyond your control, such as running out of memory, running out of disk space, or corruption in the message store.
  
## Notes to callers

Expect these return values under the following conditions.
  
|**Condition**|**Return value**|
|:-----|:-----|
|**DeleteMessages** has successfully deleted every message.  <br/> |S_OK  <br/> |
|**DeleteMessages** was unable to successfully delete every message and subfolder.  <br/> |MAPI_W_PARTIAL_COMPLETION or MAPI_E_NOT_FOUND  <br/> |
|**DeleteMessages** was unable to complete.  <br/> |Any error value except MAPI_E_NOT_FOUND  <br/> |
   
When **DeleteMessages** is unable to complete, do not assume that no work was done. **DeleteMessages** might have been able to delete one or more of the messages before encountering the error. 
  
 **DeleteMessages** returns MAPI_W_PARTIAL_COMPLETION or MAPI_E_NOT_FOUND, depending on the message store's implementation. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FolderDlg.cpp  <br/> |CFolderDlg::OnDeleteSelectedItem  <br/> |MFCMAPI uses the **IMAPIFolder::DeleteMessages** method to delete the specified messages.  <br/> |
   
## See also



[ENTRYID](entryid.md)
  
[ENTRYLIST](entrylist.md)
  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Using Macros for Error Handling](using-macros-for-error-handling.md)

