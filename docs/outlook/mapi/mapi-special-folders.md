---
title: "MAPI Special Folders"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: f2aa2376-b293-4d05-9104-218cc1fe1758
description: "Last modified: March 09, 2015"
 
 
---

# MAPI Special Folders

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
MAPI defines a few folders that are special because they serve predefined roles as default folders for certain types of messages. These special folders typically cannot be deleted, and they have special entry identifier properties.
  
There are eight special folders, some that are part of the interpersonal message (IPM) subtree. MAPI creates these folders before a client receives access to its message store, after which the client might be able to delete the folders, if necessary. Some message store providers allow deletion, while others do not. The following table describes these folders.
  
**MAPI Folders**

|**Folder**|**Description**|
|:-----|:-----|
|Outbox folder  <br/> |Contains outgoing IPM messages.  <br/> |
|Deleted Items folder  <br/> |Contains IPM messages that are marked for deletion.  <br/> |
|Sent Items folder  <br/> |Contains IPM messages that have been sent.  <br/> |
|IPM root folder  <br/> |Contains folders for managing IPM messages.  <br/> |
|Receive folder  <br/> |Contains incoming messages for a particular message class.  <br/> |
|Search-results root folder  <br/> |Contains folders for managing search results.  <br/> |
|Common-views root folder  <br/> |Contains folders for managing views for the message store.  <br/> |
|Personal-views root folder  <br/> |Contains folders for managing views for a particular user.  <br/> |
   
The first four folders relate to the IPM subtree, a tree of folders that MAPI creates when a message store is initialized. Default message stores for interactive messaging clients always include the IPM folder subtree and the other special folders in their folder hierarchy. Non-default message stores are required only to support the search-results root folder, the IPM subtree root folder, the Deleted Items folder, and the receive folder. To ensure that the IPM subtree folders exist and are valid, clients can call the [HrValidateIPMSubtree](hrvalidateipmsubtree.md) function. **HrValidateIPMSubtree** checks the folders and recreates them if there is a problem. 
  
The root folders for search results, common views, and personal views are not part of the IPM subtree; these folders are created in the root folder for the message store. The search-results root folder contains folders that support contents tables with messages that satisfy a set of search criteria. Although clients are allowed to create search-results folders in any folder, most clients designate a single root folder to be the parent of all the search-results folders created during the session. 
  
The common-views and personal-views root folders contain messages that describe views, or preferred ways of presenting message and folder data. The common-views root folder contains views that clients can use with any folder in the message store; the personal-views folder contains views that have been defined by a particular user for a particular folder or folders.
  
Clients that work with IPM messages should create all folders and messages under the IPM subtree root folder, rather than the root folder of the message store. This gives non-IPM clients — the clients that deal with messages exchanged between computers or between humans and computers — an easy way to hide their messages from IPM clients. 
  
MAPI assigns special entry identifier properties for these special folders. For a list of the special folder entry identifiers, see [Opening a Message Store Folder](opening-a-message-store-folder.md).
  
### Outlook Special Folders

Outlook special folders are identified by their entry IDs that are stored in the Inbox folder and the root folder for the message store.
  
|**Folder**|**The property to set**|
|:-----|:-----|
|Calendar  <br/> |**PR_IPM_APPOINTMENT_ENTRYID** ([PidTagIpmAppointmentEntryId](pidtagipmappointmententryid-canonical-property.md))  <br/> |
|Contacts  <br/> |**PR_IPM_CONTACT_ENTRYID** ([PidTagIpmContactEntryId](pidtagipmcontactentryid-canonical-property.md))  <br/> |
|Journal  <br/> |**PR_IPM_JOURNAL_ENTRYID** ([PidTagIpmJournalEntryId](pidtagipmjournalentryid-canonical-property.md))  <br/> |
|Notes  <br/> |**PR_IPM_NOTE_ENTRYID** ([PidTagIpmNoteEntryId](pidtagipmnoteentryid-canonical-property.md))  <br/> |
|Tasks  <br/> |**PR_IPM_TASK_ENTRYID** ([PidTagIpmTaskEntryId](pidtagipmtaskentryid-canonical-property.md))  <br/> |
|Drafts  <br/> |**PR_IPM_DRAFTS_ENTRYID** ([PidTagIpmDraftsEntryId](pidtagipmdraftsentryid-canonical-property.md))  <br/> |
   
## See also



[MAPI Folders](mapi-folders.md)

