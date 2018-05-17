---
title: "Copying or Moving a Message or a Folder"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 72290fd3-00d7-4055-bbfa-0c47b6e0f62d
description: "Last modified: November 08, 2011"
 
 
---

# Copying or Moving a Message or a Folder

 
  
**Applies to**: Outlook 
  
A client can use one of four methods to copy or move a message or a folder:
  
- [IMAPIFolder::CopyFolder](imapifolder-copyfolder.md)
    
- [IMAPIFolder::CopyMessages](imapifolder-copymessages.md)
    
- [IMAPIProp::CopyTo](imapiprop-copyto.md)
    
- [IMAPIProp::CopyProps](imapiprop-copyprops.md)
    
By setting the appropriate flags and parameters, **CopyTo** and **CopyProps** can be made to work just like **CopyFolder** or **CopyMessages**. Consider the following issues when deciding which method to call:
  
- Are you copying or moving a folder or a message?
    
- How much do you know about the folder or message to be moved or copied?
    
- How many of the folder or message's properties will be moved or copied?
    
You can use the **IMAPIProp** methods to copy or move either a folder or a message. **IMAPIFolder::CopyMessages** works with messages only; **IMAPIFolder::CopyFolder** works with folders only. 
  
Whereas using the **IMAPIFolder** methods does not require any knowledge of the properties supported by the folder or message to be copied or moved, you must have some knowledge to use the **IMAPIProp** methods. With **IMAPIProp::CopyProps**, you must be able to explicitly specify which of the folder or message properties that you want to copy or move. With **IMAPIProp::CopyTo**, unless you want to copy or move all of the properties, you must explicitly specify which ones should be excluded. For more information about these methods, see [Copying MAPI Properties](copying-mapi-properties.md).
  
The number of properties to be copied or moved can affect your decision as to which method to use. If you are copying or moving multiple messages, call **IMAPIFolder::CopyMessages**. An alternate choice is to call **IMAPIProp::CopyProps** to copy only the folder's **PR_CONTAINER_CONTENTS** ( [PidTagContainerContents](pidtagcontainercontents-canonical-property.md)) property. The following procedure shows how to use **CopyMessages**. 
  
 **To copy or move one or more messages**
  
1. Locate valid entry identifiers for the source and destination folders.
    
2. Open these folders in read/write mode by calling either [IMAPISession::OpenEntry](imapisession-openentry.md) or [IMsgStore::OpenEntry](imsgstore-openentry.md) and setting the MAPI_MODIFY flag. 
    
3. Check that the interface pointer returned from **OpenEntry** is an **IMAPIFolder** interface pointer. If not, cast it to the LPMAPIFOLDER type. 
    
4. Create an array of entry identifiers representing the one or more messages to be copied or moved. 
    
5. Call **IMAPIFolder::CopyMessages** with the following flags set: 
    
  - MESSAGE_MOVE, if you want to perform a move operation. 
    
  - MESSAGE_DIALOG and pass a window handle in the  _ulUIParam_ parameter, if you want the folder to show a progress indicator. 
    
6. Release the **IMAPIFolder** pointers for the source and destination folders. 
    
If you want to copy the complete contents of a folder to another folder, call the source folder's **IMAPIFolder::CopyFolder** or **IMAPIProp::CopyTo** method. 
  
To copy a few of a folder's properties, call its **IMAPIProp::CopyProps** method. To copy most of a folder's properties, call **IMAPIProp::CopyTo**. 
  
For example, if you want to copy a folder's **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) and **PR_COMMENT** ( [PidTagComment](pidtagcomment-canonical-property.md)) properties, you have the following options:
  
- Call **IMAPIFolder::CopyFolder** to copy all of the folder properties and then delete the unwanted ones from the new folder. 
    
- Call **CopyTo** and exclude all of the folder's properties except for **PR_DISPLAY_NAME** and **PR_COMMENT**. 
    
- Call **CopyProps**, passing **PR_DISPLAY_NAME** and **PR_COMMENT** in the include array. 
    
In this case, **CopyProps** is the best choice because it is meant to be used to copy a small set of properties and is the easiest call to implement. 
  
To copy or move only folder properties, without including messages, call the folder's **IMAPIProp::CopyTo** method and exclude the following properties: 
  
- **PR_CONTAINER_CONTENTS** ( [PidTagContainerContents](pidtagcontainercontents-canonical-property.md))
    
- **PR_FOLDER_ASSOCIATED_CONTENTS** ( [PidTagFolderAssociatedContents](pidtagfolderassociatedcontents-canonical-property.md))
    
The copy methods can return S_OK, indicating total success, MAPI_W_PARTIAL_COMPLETION, indicating partial success, or an error. If MAPI_W_PARTIAL_COMPLETION is returned, use the **HR_FAILED** macro to access a more specific error. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
  
If you copy messages from one message store to another and Unicode is not supported by both, be aware that information can be lost due to code page conversion. Usually you cannot know if the message stores support one or both formats, making it impossible to determine whether to copy text properties as ASCII strings or as Unicode strings. If you support Unicode, try to perform a Unicode copy; if it fails with the error value MAPI_E_BAD_CHARWIDTH, resort to ASCII.
  

