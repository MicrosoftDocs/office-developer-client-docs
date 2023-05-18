---
title: "IMAPISupportCopyFolder"
description: "IMAPISupportCopyFolder copies or moves a folder from its current parent folder to another parent folder."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.CopyFolder
api_type:
- COM
ms.assetid: c2e0939f-0668-473f-856c-a27af094070b
---

# IMAPISupport::CopyFolder

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Copies or moves a folder from its current parent folder to another parent folder.
  
```cpp
HRESULT CopyFolder(
  LPCIID lpSrcInterface,
  LPVOID lpSrcFolder,
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

 _lpSrcInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the parent folder of the folder to be copied or moved.
    
 _lpSrcFolder_
  
> [in] A pointer to the parent folder of the folder to be copied or moved. 
    
 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by  _lpEntryID_.
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the folder to be copied or moved. 
    
 _lpInterface_
  
> [in] Reserved; must be NULL.
    
 _lpDestFolder_
  
> [in] A pointer to the folder that is to receive the folder to be copied or moved.
    
 _lpszNewFolderName_
  
> [in] A pointer to the name of the copied or moved folder; otherwise, NULL, which indicates that the copied or moved folder should have the same name as the source folder (the folder pointed to by  _lpEntryID_).
    
 _ulUIParam_
  
> [in] A handle of the window for the progress indicator dialog box and related windows. The  _ulUIParam_ parameter is ignored unless the FOLDER_DIALOG flag is set in the _ulFlags_ parameter. 
    
 _lpProgress_
  
> [in] A pointer to a progress object that displays a progress indicator. If NULL is passed in  _lpProgress_, the message store provider displays a progress indicator by using the MAPI progress object implementation. The  _lpProgress_ parameter is ignored unless the FOLDER_DIALOG flag is set in  _ulFlags_.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the copy or move operation is accomplished. The following flags can be set:
    
COPY_SUBFOLDERS 
  
> All of the folder's subfolders should be copied or moved. When COPY_SUBFOLDERS is not set for a copy operation, only the folder identified by  _lpEntryID_ is copied. With a move operation, the COPY_SUBFOLDERS behavior is the default regardless of whether the flag is set. 
    
FOLDER_DIALOG 
  
> Requests the display of a progress indicator.
    
FOLDER_MOVE 
  
> The folder should be moved instead of copied. If FOLDER_MOVE is not set, the folder is copied.
    
MAPI_UNICODE 
  
> The name of the folder is in Unicode format. If the MAPI_UNICODE flag is not set, the name of the folder is in ANSI format.
    
## Return value

S_OK 
  
> The folder has been successfully copied or moved.
    
MAPI_E_COLLISION 
  
> The name of the folder being moved or copied is the same as that of a subfolder in the destination folder. The message store provider requires that folder names be unique. The operation stops without completing.
    
MAPI_W_PARTIAL_COMPLETION 
  
> The call succeeded, but not all entries were successfully copied. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPISupport::CopyFolder** method is implemented for message store provider support objects. Message store providers can call **IMAPISupport::CopyFolder** in their implementation of [IMAPIFolder::CopyFolder](imapifolder-copyfolder.md) to copy or move a single folder from one parent folder to another. 
  
 **IMAPISupport::CopyFolder** adds the copied or moved folder as a subfolder of the destination folder. 
  
## Notes to callers

 **IMAPISupport::CopyFolder** allows simultaneous renaming and moving of folders and the copying or moving of subfolders of the affected folder. To copy or move all subfolders nested in the copied or moved folder, pass the COPY_SUBFOLDERS flag in  _ulFlags_. 
  
Expect the following return values under the following conditions:
  
|**Condition**|**Return value**|
|:-----|:-----|
|**CopyFolder** successfully copied or moved the folder and all its subfolders, if applicable. |S_OK  <br/> |
|**CopyFolder** was unable to successfully copy or move all of the folders. |MAPI_W_PARTIAL_COMPLETION  <br/> |
|**CopyFolder** was unable to complete. |Any error value  <br/> |
   
If **CopyFolder** returns an error value, do not proceed on the assumption that no work was done. One or more folders could have been copied or moved before **CopyFolder** experienced the failure. 
  
## See also



[IMAPISupport : IUnknown](imapisupportiunknown.md)

