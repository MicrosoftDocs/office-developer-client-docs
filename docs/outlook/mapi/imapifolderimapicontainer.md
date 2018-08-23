---
title: "IMAPIFolder  IMAPIContainer"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFolder
api_type:
- COM
ms.assetid: bc2e8d17-7687-43c2-8f01-b677703f7288
description: "Last modified: March 09, 2015"
---

# IMAPIFolder : IMAPIContainer

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Performs operations on the messages and subfolders in a folder.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Folder objects  <br/> |
|Implemented by:  <br/> |Message store providers  <br/> |
|Called by:  <br/> |Client applications and MAPI  <br/> |
|Interface identifier:  <br/> |IID_IMAPIFolder  <br/> |
|Pointer type:  <br/> |LPMAPIFOLDER  <br/> |
|Transaction model:  <br/> |Nontransacted  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[CreateMessage](imapifolder-createmessage.md) <br/> |Creates a new message.  <br/> |
|[CopyMessages](imapifolder-copymessages.md) <br/> |Copies or moves one or more messages.  <br/> |
|[DeleteMessages](imapifolder-deletemessages.md) <br/> |Deletes one or more messages.  <br/> |
|[CreateFolder](imapifolder-createfolder.md) <br/> |Creates a new subfolder.  <br/> |
|[CopyFolder](imapifolder-copyfolder.md) <br/> |Copies or moves a subfolder.  <br/> |
|[DeleteFolder](imapifolder-deletefolder.md) <br/> |Deletes a subfolder.  <br/> |
|[SetReadFlags](imapifolder-setreadflags.md) <br/> |Sets or clears the MSGFLAG_READ flag in the **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property of one or more of the folder's messages, and manages the sending of read reports.  <br/> |
|[GetMessageStatus](imapifolder-getmessagestatus.md) <br/> |Obtains the status associated with a message in a particular folder.  <br/> |
|[SetMessageStatus](imapifolder-setmessagestatus.md) <br/> |Sets the status associated with a message.  <br/> |
|[SaveContentsSort](imapifolder-savecontentssort.md) <br/> |Sets the default sort order for a folder's contents table.  <br/> |
|[EmptyFolder](imapifolder-emptyfolder.md) <br/> |Deletes all messages and subfolders from a folder without deleting the folder itself.  <br/> |
   
|**Required properties**|**Access**|
|:-----|:-----|
|**PR_DISPLAY_NAME** ([PidTagDisplayNamePrefix](pidtagdisplaynameprefix-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_FOLDER_TYPE** ([PidTagFolderType](pidtagfoldertype-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_PARENT_ENTRYID** ([PidTagParentEntryId](pidtagparententryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_STORE_ENTRYID** ([PidTagStoreEntryId](pidtagstoreentryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_STORE_RECORD_KEY** ([PidTagStoreRecordKey](pidtagstorerecordkey-canonical-property.md))  <br/> |Read-only  <br/> |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

