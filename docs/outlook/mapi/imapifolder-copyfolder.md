---
title: "IMAPIFolderCopyFolder"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFolder.CopyFolder
api_type:
- COM
ms.assetid: 2c1c25c6-1aec-4d9e-a2a3-bf1b4a2908b8
description: "Last modified: March 09, 2015"
---

# IMAPIFolder::CopyFolder

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Copies or moves a subfolder.
  
```
HRESULT CopyFolder(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPCIID lpInterface,
  LPVOID lpDestFolder,
  LPSTR lpszNewFolderName,
  ULONG_PTR ulUIParam,
  LPMAPIPROGRESS lpProgress,
  ULONG ulFlags
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the subfolder to copy or move.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the folder that the  _lpDestFolder_ parameter points to. Passing NULL causes the service provider to return the standard folder interface, [IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md). Valid values for  _lpInterface_ include IID_IUnknown, IID_IMAPIProp, IID_IMAPIContainer, and IID_IMAPIFolder. 
    
 _lpDestFolder_
  
> [in] A pointer to the open folder to receive the copied or moved subfolder.
    
 _lpszNewFolderName_
  
> [in] A pointer to the name of the copied or moved folder in its new destination. If  _lpszNewFolderName_ is set to NULL, the name of the source subfolder is used for the name of the destination folder. 
    
 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator. The  _ulUIParam_ parameter is ignored unless the FOLDER_DIALOG flag in the  _ulFlags_ parameter is set. 
    
 _lpProgress_
  
> [in] A pointer to a progress object that displays a progress indicator. If NULL is passed in  _lpProgress_, the message store provider displays a progress indicator by using the MAPI progress object implementation. The  _lpProgress_ parameter is ignored unless the FOLDER_DIALOG flag is set in  _ulFlags_.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the copy or move operation. The following flags can be set:
    
COPY_SUBFOLDERS 
  
> All of the subfolders in the subfolder to be copied should also be copied. When COPY_SUBFOLDERS is not set for a copy operation, only the subfolder identified by  _lpEntryID_ is copied. With a move operation, the COPY_SUBFOLDERS behavior is the default regardless of whether the flag is set. 
    
FOLDER_DIALOG 
  
> Requests the display of a progress indicator.
    
FOLDER_MOVE 
  
> The subfolder is to be moved instead of copied. If FOLDER_MOVE is not set, the subfolder is copied.
    
MAPI_DECLINE_OK 
  
> Informs the message store provider that if it implements **CopyFolder** by calling its support object's [IMAPISupport::DoCopyTo](imapisupport-docopyto.md) or [IMAPISupport::DoCopyProps](imapisupport-docopyprops.md) method, **CopyFolder** should instead immediately return MAPI_E_DECLINE_COPY. 
    
MAPI_UNICODE 
  
> The name of the destination folder is in Unicode format. If the MAPI_UNICODE flag is not set, the folder name is in ANSI format.
    
## Return value

S_OK 
  
> The specified folder has been successfully copied or moved.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the message store provider does not support Unicode, or MAPI_UNICODE was not set and the message store provider supports only Unicode.
    
MAPI_E_COLLISION 
  
> The name of the folder being moved or copied is the same as that of a subfolder in the destination folder. The message store provider requires unique folder names.
    
MAPI_E_DECLINE_COPY 
  
> The provider implements this method by calling a support object method, and the caller has passed the MAPI_DECLINE_OK flag.
    
MAPI_E_FOLDER_CYCLE 
  
> The source folder directly or indirectly contains the destination folder. Significant work may have been performed before this condition was discovered, so the source and destination folder may be partially modified. 
    
MAPI_W_PARTIAL_COMPLETION 
  
> The call succeeded, but not all entries were successfully copied. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPIFolder::CopyFolder** method copies or moves a subfolder from one location to another. The subfolder being copied or moved is added to the destination folder as a subfolder. 
  
## Notes to Implementers

When the copy or move operation involves more than one folder, as indicated by setting the COPY_SUBFOLDERS flag, perform the operation as completely as possible for each folder. Sometimes one of the folders to be moved or copied does not exist or has already been moved or copied elsewhere. Do not stop the operation prematurely unless a failure occurs that is beyond your control, such as running out of memory, running out of disk space, or corruption in the message store.
  
Try to retain all message entry identifiers in the copied messages. You should also try to preserve entry identifiers, but it is not required. 
  
## Notes to Callers

Expect these return values under the following conditions.
  
|**Condition**|**Return value**|
|:-----|:-----|
|**CopyFolder** has successfully copied or moved every message and subfolder.  <br/> |S_OK  <br/> |
|**CopyFolder** was unable to successfully copy or move every message and subfolder.  <br/> |MAPI_W_PARTIAL_COMPLETION or MAPI_E_NOT_FOUND  <br/> |
|**CopyFolder** was unable to complete.  <br/> |Any error value except MAPI_E_NOT_FOUND  <br/> |
   
When **CopyFolder** is unable to complete, do not assume that no work was done. **CopyFolder** might have been able to copy or move one or more of the messages and subfolders before encountering the error. 
  
If an entry identifier for a folder that does not exist is passed in  _lpEntryID_, **CopyFolder** returns MAPI_W_PARTIAL_COMPLETION or MAPI_E_NOT_FOUND, depending on the message store's implementation. 
  
Depending on the message store provider, the entry identifier of the original message may or may not be preserved in the copied message. You should preserve entry identifiers whenever possible, but it is not a requirement. You can generally depend on the following scenarios:
  
- When you move a folder between two different types of message stores, the entry identifier is guaranteed to change.
    
- When you move a folder between two message stores of the same type, the entry identifier almost always changes.
    
- When you move a folder to another location in the same message store, the entry identifier may or may not change, depending on the message store provider.
    
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MsgStoreDlg.cpp  <br/> |CMsgStoreDlg::OnPasteFolder  <br/> |MFCMAPI uses the **IMAPIFolder::CopyFolder** method to copy folders from one location to another. MFCMAPI remembers the source folder during the copy operation and actually performs the copy during the paste operation.  <br/> |
   
## See also

#### Reference

[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

