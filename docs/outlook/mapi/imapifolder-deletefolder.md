---
title: "IMAPIFolderDeleteFolder"
description: "IMAPIFolderDeleteFolder deletes a subfolder. This article describes its syntax, parameters, return value, and remarks."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFolder.DeleteFolder
api_type:
- COM
ms.assetid: 6c3e883c-80c0-4eda-8f81-8277d933a74b
---

# IMAPIFolder::DeleteFolder

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Deletes a subfolder.
  
```cpp
HRESULT DeleteFolder(
  ULONG_PTR cbEntryID,
  LPENTRYID lpEntryID,
  ULONG_PTR ulUIParam,
  LPMAPIPROGRESS lpProgress,
  ULONG ulFlags
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the subfolder to delete.
    
 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator. The  _ulUIParam_ parameter is ignored unless the FOLDER_DIALOG flag is set in the _ulFlags_ parameter. 
    
 _lpProgress_
  
> [in] A pointer to a progress object that displays a progress indicator. If NULL is passed in  _lpProgress_, the message store provider displays a progress indicator by using the MAPI progress object implementation. The  _lpProgress_ parameter is ignored unless the FOLDER_DIALOG flag is set in  _ulFlags_.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the deletion of the subfolder. The following flags can be set:
    
DEL_FOLDERS 
  
> All subfolders of the subfolder pointed to by  _lpEntryID_ should be deleted. 
    
DEL_MESSAGES 
  
> All messages in the subfolder pointed to by  _lpEntryID_ should be deleted. 
    
DELETE_HARD_DELETE
  
> Permanently removes the folder.
    
FOLDER_DIALOG 
  
> A progress indicator should be displayed while the operation proceeds.
    
## Return value

S_OK 
  
> The specified folder has been successfully deleted.
    
MAPI_E_HAS_FOLDERS 
  
> The subfolder being deleted contains subfolders, and the DEL_FOLDERS flag was not set. The subfolders were not deleted.
    
MAPI_E_HAS_MESSAGES 
  
> The subfolder being deleted contains messages, and the DEL_MESSAGES flag was not set. The subfolder was not deleted.
    
MAPI_W_PARTIAL_COMPLETION 
  
> The call succeeded, but not all of the entries were successfully deleted. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPIFolder::DeleteFolder** method deletes a subfolder. By default, **DeleteFolder** operates only on empty folders, but you can use it successfully on non-empty folders by setting two flags: DEL_FOLDERS and DEL_MESSAGES. Only empty folders or folders that set both the DEL_FOLDERS and DEL_MESSAGES flags on the **DeleteFolder** call can be deleted. DEL_FOLDERS enables all of the folder's subfolders to be removed; DEL_MESSAGES enables all of the folder's messages to be removed. 
  
The MFCMAPI program allows to choose between folder soft-delete vs. folder hard-delete. Exchange Server 2019 does not implement folder soft-delete in private stores either, and treats deletion requests for folders within private stores (cf. the [[ropOpenFolder]](/openspecs/exchange_server_protocols/ms-oxcfold/9a9402e4-0694-4043-aee0-bcb9737cc8c0) request) as if DELETE_HARD_DELETE was set.
  
## Notes to implementers

When the delete operation involves more than one folder, perform the operation as completely as possible for each folder. Sometimes one of the folders to be deleted does not exist or has been moved or copied elsewhere. Do not stop the operation prematurely unless a failure occurs that is beyond your control, such as running out of memory, running out of disk space, or corruption in the message store.
  
## Notes to callers

Expect these return values under the following conditions.
  
|**Condition**|**Return value**|
|:-----|:-----|
|**DeleteFolder** has successfully deleted every message and subfolder. |S_OK  <br/> |
|**DeleteFolder** was unable to successfully delete every message and subfolder. |MAPI_W_PARTIAL_COMPLETION or MAPI_E_NOT_FOUND  <br/> |
|**DeleteFolder** was unable to complete. |Any error value except MAPI_E_NOT_FOUND  <br/> |
   
When **DeleteFolder** is unable to complete, do not assume that no work was done. **DeleteFolder** might have been able to delete one or more of the messages and subfolders before encountering the error. 
  
If one or more subfolders cannot be deleted, **DeleteFolder** returns MAPI_W_PARTIAL_COMPLETION or MAPI_E_NOT_FOUND, depending on the message store provider's implementation. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MsgStoreDlg.cpp  <br/> |CMsgStoreDlg::OnDeleteSelectedItem  <br/> |MFCMAPI uses the **IMAPIFolder::DeleteFolder** method to delete folders. |
   
## See also



[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

