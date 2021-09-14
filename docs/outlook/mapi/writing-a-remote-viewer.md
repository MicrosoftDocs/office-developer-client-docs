---
title: "Writing a remote viewer"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: f4d7d42f-688a-4199-b972-dd42528c0cdf
description: "Last modified: March 09, 2015"
---

# Writing a remote viewer

**Applies to**: Outlook 2013 | Outlook 2016 
  
A remote viewer is a window in a client application that provides controlled access to messages stored on another computer. This controlled access might operate on a slow communications link. Rather than retrieve a complete selection of available messages every time a user opens a folder, the remote viewer first displays only the headers. The user then selects from the headers which of the messages to display in full. Remote viewer clients can allow their users to delete messages before they are ever downloaded. 
  
## To retrieve the headers of messages stored remotely
  
1. Call [IMAPISession::GetStatusTable](imapisession-getstatustable.md) to access the status table. 
    
2. Call [IMAPITable::Restrict](imapitable-restrict.md) to limit the status table to only those rows that have their **PR\_RESOURCE\_TYPE** ([PidTagResourceType](pidtagresourcetype-canonical-property.md)) column set to MAPI\_TRANSPORT\_PROVIDER. 
    
3. Call [IMAPITable::SetColumns](imapitable-setcolumns.md) to include the following columns in the status table: 
   - **PR\_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))
   - **PR\_RESOURCE\_METHODS** ([PidTagResourceMethods](pidtagresourcemethods-canonical-property.md))
   - **PR\_RESOURCE\_TYPE**, **PR\_PROVIDER\_DISPLAY** ([PidTagProviderDisplay](pidtagproviderdisplay-canonical-property.md))
   - **PR\_STATUS\_CODE** ([PidTagStatusCode](pidtagstatuscode-canonical-property.md)).
    
4. Call [HrQueryAllRows](hrqueryallrows.md) to retrieve all the rows in the status table. 
    
5. Pass the entry identifier for each row in the table in a call to [IMAPISession::OpenEntry](imapisession-openentry.md). Because this interface is marshaled from the MAPI spooler's process context to the client's process context — unlike interfaces typically obtained from address book or message store providers — issues concerning multithreading are of more importance. 
    
6. Call the status object's [IUnknown::QueryInterface](https://msdn.microsoft.com/library/54d5ff80-18db-43f2-b636-f93ac053146d.aspx) method, passing IID_IMAPIFolder as the interface identifier, to retrieve the remote folder. The remote folder is not a complete folder implementation; it supports only a subset of folder methods and properties. One of the required methods, [IMAPIProp::GetProps](imapiprop-getprops.md), supports the retrieval of the following properties:
    
    |||
    |:-----|:-----|
    |**PR\_ACCESS** ([PidTagAccess](pidtagaccess-canonical-property.md))  <br/> |**PR_ACCESS_LEVEL** ([PidTagAccessLevel](pidtagaccesslevel-canonical-property.md))  <br/> |
    |**PR_CONTENT_COUNT** ([PidTagContentCount](pidtagcontentcount-canonical-property.md))  <br/> |**PR_ASSOC_CONTENT_COUNT** ([PidTagAssociatedContentCount](pidtagassociatedcontentcount-canonical-property.md))  <br/> |
    |**PR_FOLDER_TYPE** ([PidTagFolderType](pidtagfoldertype-canonical-property.md))  <br/> |**PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |
    |**PR\_SUBFOLDERS** ([PidTagSubfolders](pidtagsubfolders-canonical-property.md))  <br/> |**PR_CREATION_TIME** ([PidTagCreationTime](pidtagcreationtime-canonical-property.md))  <br/> |
    |**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |**PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md))  <br/> |
    
    Remote folders must also support the [IMAPIProp::GetPropList](imapiprop-getproplist.md), [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md), and [IMAPIFolder::SetMessageStatus](imapifolder-setmessagestatus.md) methods. Remote folder contents tables typically support the following columns: 
        
    |||
    |:-----|:-----|
    |**PR\_DISPLAY\_TO** ([PidTagDisplayTo](pidtagdisplayto-canonical-property.md))  <br/> |**PR\_ENTRYID** <br/> |
    |**PR\_HASATTACH** ([PidTagHasAttachments](pidtaghasattachments-canonical-property.md))  <br/> |**PR_IMPORTANCE** ([PidTagImportance](pidtagimportance-canonical-property.md))  <br/> |
    |**PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md))  <br/> |**PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md))  <br/> |
    |**PR\_MESSAGE_DELIVERY_TIME** ([PidTagMessageDeliveryTime](pidtagmessagedeliverytime-canonical-property.md))  <br/> |**PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md))  <br/> |
    |**PR\_MESSAGE_DOWNLOAD_TIME** ([PidTagMessageDownloadTime](pidtagmessagedownloadtime-canonical-property.md))  <br/> |**PR_MESSAGE_SIZE** ([PidTagMessageSize](pidtagmessagesize-canonical-property.md))  <br/> |
    |**PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md))  <br/> |**PR_OBJECT_TYPE** <br/> |
    |**PR_NORMALIZED_SUBJECT** ([PidTagNormalizedSubject](pidtagnormalizedsubject-canonical-property.md))  <br/> |**PR_PRIORITY** ([PidTagPriority](pidtagpriority-canonical-property.md))  <br/> |
    |**PR_SENDER_NAME** ([PidTagSenderName](pidtagsendername-canonical-property.md))  <br/> |**PR_SENSITIVITY** ([PidTagSensitivity](pidtagsensitivity-canonical-property.md))  <br/> |
    |**PR\_SENT_REPRESENTING_NAME** ([PidTagSentRepresentingName](pidtagsentrepresentingname-canonical-property.md))  <br/> |**PR_SUBJECT** ([PidTagSubject](pidtagsubject-canonical-property.md))  <br/> |
   
7. Call the transport provider's [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method the first time that one of the transfer options is picked. Either the REFRESH_XP_HEADER_CACHE or PROCESS_XP_HEADER_CACHE process flag should be set as well as the SHOW_XP_SSESSION_UI flag to allow the user interface to be shown. 
    
   > [!NOTE]
   > To mark a particular message header for downloading or deletion, a client calls [IMAPIFolder::SetMessageStatus](imapifolder-setmessagestatus.md) and sets either the MSGSTATUS_REMOTE_DOWNLOAD or MSGSTATUS_REMOTE_DELETE flag. 
  

