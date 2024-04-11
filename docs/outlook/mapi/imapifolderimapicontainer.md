---
title: "IMAPIFolder  IMAPIContainer"
description: "IMAPIFolderIMAPIContainer performs operations on the messages and subfolders in a folder. This article describes the related properties and members."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFolder
api_type:
- COM
ms.assetid: bc2e8d17-7687-43c2-8f01-b677703f7288
---

# IMAPIFolder : IMAPIContainer

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Performs operations on the messages and subfolders in a folder.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Folder objects  <br/> |
|Implemented by:  <br/> |Message store providers  <br/> |
|Called by:  <br/> |Client applications and MAPI  <br/> |
|Interface identifier:  <br/> |IID_IMAPIFolder  <br/> |
|Pointer type:  <br/> |LPMAPIFOLDER  <br/> |
|Transaction model:  <br/> |Nontransacted  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[CreateMessage](imapifolder-createmessage.md) <br/> |Creates a new message. |
|[CopyMessages](imapifolder-copymessages.md) <br/> |Copies or moves one or more messages. |
|[DeleteMessages](imapifolder-deletemessages.md) <br/> |Deletes one or more messages. |
|[CreateFolder](imapifolder-createfolder.md) <br/> |Creates a new subfolder. |
|[CopyFolder](imapifolder-copyfolder.md) <br/> |Copies or moves a subfolder. |
|[DeleteFolder](imapifolder-deletefolder.md) <br/> |Deletes a subfolder. |
|[SetReadFlags](imapifolder-setreadflags.md) <br/> |Sets or clears the MSGFLAG_READ flag in the **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property of one or more of the folder's messages, and manages the sending of read reports. |
|[GetMessageStatus](imapifolder-getmessagestatus.md) <br/> |Obtains the status associated with a message in a particular folder. |
|[SetMessageStatus](imapifolder-setmessagestatus.md) <br/> |Sets the status associated with a message. |
|[SaveContentsSort](imapifolder-savecontentssort.md) <br/> |Sets the default sort order for a folder's contents table. |
|[EmptyFolder](imapifolder-emptyfolder.md) <br/> |Deletes all messages and subfolders from a folder without deleting the folder itself. |
   
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

