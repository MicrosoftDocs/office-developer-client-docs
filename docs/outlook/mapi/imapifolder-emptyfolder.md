---
title: "IMAPIFolderEmptyFolder"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFolder.EmptyFolder
api_type:
- COM
ms.assetid: 4cfcb498-9182-4906-bd6f-d9bc387bc88b
description: "Last modified: March 09, 2015"
---

# IMAPIFolder::EmptyFolder

  
  
**Applies to**: Outlook 
  
Deletes all messages and subfolders from a folder without deleting the folder itself.
  
```cpp
HRESULT EmptyFolder(
  ULONG_PTR ulUIParam,
  LPMAPIPROGRESS lpProgress,
  ULONG ulFlags
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator. The  _ulUIParam_ parameter is ignored unless the FOLDER_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _lpProgress_
  
> [in] A pointer to a progress object that displays a progress indicator. If NULL is passed in  _lpProgress_, the message store provider displays a progress indicator by using the MAPI progress object implementation. The  _lpProgress_ parameter is ignored unless the FOLDER_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the folder is emptied. The following flags can be set:
    
DEL_ASSOCIATED 
  
> Deletes all subfolders, including subfolders that contain messages with associated content. The DEL_ASSOCIATED flag has meaning only for the top-level folder the call acts on.
    
DELETE_HARD_DELETE
  
> Permanently removes all messages, including soft-deleted ones.
    
FOLDER_DIALOG 
  
> Displays a progress indicator while the operation proceeds.
    
## Return value

S_OK 
  
> The folder was successfully emptied.
    
MAPI_W_PARTIAL_COMPLETION 
  
> The call succeeded, but the folder was not completely emptied. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPIFolder::EmptyFolder** method deletes all of a folder's contents without deleting the folder itself. 
  
During an **EmptyFolder** call, submitted messages are not deleted. 
  
A folder's associated contents include messages that are used to describe views, rules, custom forms, and custom solution storage, and can also include form definitions. 
  
## Notes to implementers

Do not call the [IMsgStore::AbortSubmit](imsgstore-abortsubmit.md) method for messages in the folder that have been submitted. Submitted messages are not deleted. 
  
## Notes to callers

Expect these return values under the following conditions.
  
|**Condition**|**Return value**|
|:-----|:-----|
|**EmptyFolder** has successfully emptied the folder.  <br/> |S_OK  <br/> |
|**EmptyFolder** was unable to completely empty the folder.  <br/> |MAPI_W_PARTIAL_COMPLETION  <br/> |
|**EmptyFolder** was unable to complete.  <br/> |Any error value  <br/> |
   
When **EmptyFolder** is unable to complete, do not assume that no work was done. **EmptyFolder** might have been able to delete some of the folder's contents before encountering the error. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MsgStoreDlg.cpp  <br/> |CMsgStoreDlg::OnEmptyFolder  <br/> |MFCMAPI uses the **IMAPIFolder::EmptyFolder** method to delete the contents of the specified folder.  <br/> |
   
## See also



[IMsgStore::AbortSubmit](imsgstore-abortsubmit.md)
  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Using Macros for Error Handling](using-macros-for-error-handling.md)

