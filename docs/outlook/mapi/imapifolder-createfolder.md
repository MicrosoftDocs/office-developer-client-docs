---
title: "IMAPIFolderCreateFolder"
description: "IMAPIFolderCreateFolder creates a new subfolder. This article describes its syntax, parameters, return value, and remarks."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFolder.CreateFolder
api_type:
- COM
ms.assetid: 39d07fc8-09aa-4122-af32-b02f2c893d29
---

# IMAPIFolder::CreateFolder

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a new subfolder.
  
```cpp
HRESULT CreateFolder(
  ULONG ulFolderType,
  LPSTR lpszFolderName,
  LPSTR lpszFolderComment,
  LPCIID lpInterface,
  ULONG ulFlags,
  LPMAPIFOLDER FAR * lppFolder
);
```

## Parameters

 _ulFolderType_
  
> [in] The type of folder to create. The following flags can be set:
    
FOLDER_GENERIC 
  
> A generic folder should be created.
    
FOLDER_SEARCH 
  
> A search-results folder should be created.
    
 _lpszFolderName_
  
> [in] A pointer to a string that contains the name for the new folder. This name is the basis for the new folder's **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property.
    
 _lpszFolderComment_
  
> [in] A pointer to a string that contains a comment associated with the new folder. This string becomes the value of the new folder's **PR_COMMENT** ([PidTagComment](pidtagcomment-canonical-property.md)) property. If NULL is passed, the folder has no initial comment.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the new folder. Passing NULL causes the message store provider to return the standard folder interface, [IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md). Clients must pass NULL. Other callers can set the  _lpInterface_ parameter to IID_IUnknown, IID_IMAPIProp, IID_IMAPIContainer, or IID_IMAPIFolder. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the folder is created. The following flags can be set:
    
MAPI_DEFERRED_ERRORS 
  
> Allows **CreateFolder** to return successfully, possibly before the new folder is fully available to the calling client. If the new folder is not available, making a subsequent call to it can cause an error. 
    
MAPI_UNICODE 
  
> The name of the folder is in Unicode format. If the MAPI_UNICODE flag is not set, the folder name is in ANSI format.
    
OPEN_IF_EXISTS 
  
> Allows the method to succeed even if the folder named in the _lpszFolderName_ parameter already exists by opening the existing folder that has that name. Note that message store providers that allow sibling folders to have the same name might not open an existing folder if more than one exists with the supplied name. 
    
 _lppFolder_
  
> [out] A pointer to a pointer to the newly created folder.
    
## Return value

S_OK 
  
> The new folder has been successfully created or opened, if the OPEN_IF_EXISTS flag is set.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
MAPI_E_COLLISION 
  
> A folder that has the name given in the _lpszFolderName_ parameter already exists. Folder names must be unique. 
    
## Remarks

The **IMAPIFolder::CreateFolder** method creates a subfolder in the current folder and assigns an entry identifier to the new folder. 
  
## Notes to callers

When **CreateFolder** returns, be aware that the entry identifier for the new folder might not be available. Some message store providers do not make entry identifiers available until after you have called the new folder's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method to permanently save it. This is especially true if you have set the MAPI_DEFERRED_ERRORS flag. 
  
Be aware that some message store providers always point the  _lppFolder_ parameter to the folder's standard interface, regardless of the value that you pass in for the  _lpInterface_ parameter. Because the interface pointer that is returned might not be of the type that you expect, call the new folder's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve the **PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md)) property. If necessary, cast the pointer to a more appropriate type before you make other calls.
  
Most message store providers require the name of the new folder to be unique with respect to the names of its sibling folders. Be able to handle the MAPI_E_COLLISION error value, which is returned if this rule is not followed. 
  
To determine the entry identifier of the newly created folder, call the new folder's **IMAPIProp::GetProps** method to retrieve its **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MsgStoreDlg.cpp  <br/> |CMsgStoreDlg::OnCreateSubFolder  <br/> |MFCMAPI uses the **CMsgStoreDlg::OnCreateSubFolder** method to create new folders in MFCMAPI. |
   
## See also



[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

