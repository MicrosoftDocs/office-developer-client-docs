---
title: "Opening a message store folder"
description: "Describes the entry identifier folders and properties, which must be available before any folder can be opened."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: d858e4fe-822e-4330-9ed3-4b7d22fa51dc
---

# Opening a message store folder

**Applies to**: Outlook 2013 | Outlook 2016 
  
Before any folder can be opened, its entry identifier must be available. For most folders, this means retrieving their **PR_ENTRYID** properties. For special folders, such as some of the IPM subtree folders and other root folders, MAPI defines special entry identifier properties that are accessible by calling the message store's **IMAPIProp::GetProps** method. These entry identifiers are always long-term and are named as follows: 
  
|**Folder**|**Entry identifier property**|
|:-----|:-----|
|Outbox folder  <br/> |**PR_IPM_OUTBOX_ENTRYID** ([PidTagIpmOutboxEntryId](pidtagipmoutboxentryid-canonical-property.md)) (IPM message class only)  <br/> |
|Deleted Items folder  <br/> |**PR_IPM_WASTEBASKET_ENTRYID** ([PidTagIpmWastebasketEntryId](pidtagipmwastebasketentryid-canonical-property.md))  <br/> |
|Sent Items folder  <br/> |**PR_IPM_SENTMAIL_ENTRYID** ([PidTagIpmSentMailEntryId](pidtagipmsentmailentryid-canonical-property.md))  <br/> |
|IPM root folder  <br/> |**PR_IPM_SUBTREE_ENTRYID** ([PidTagIpmSubtreeEntryId](pidtagipmsubtreeentryid-canonical-property.md))  <br/> |
|Search-results root folder  <br/> |**PR_FINDER_ENTRYID** ([PidTagFinderEntryId](pidtagfinderentryid-canonical-property.md))  <br/> |
|Common views root folder  <br/> |**PR_COMMON_VIEWS_ENTRYID** ([PidTagCommonViewsEntryId](pidtagcommonviewsentryid-canonical-property.md))  <br/> |
|Personal views root folder  <br/> |**PR_VIEWS_ENTRYID** ([PidTagViewsEntryId](pidtagviewsentryid-canonical-property.md))  <br/> |
|Contacts root folder  <br/> |**PR_IPM_CONTACT_ENTRYID** ([PidTagIpmContactEntryId](pidtagipmcontactentryid-canonical-property.md))  <br/> |
|Drafts root folder  <br/> |**PR_IPM_DRAFTS_ENTRYID** ([PidTagIpmDraftsEntryId](pidtagipmdraftsentryid-canonical-property.md))  <br/> |
|Journal root folder  <br/> |**PR_IPM_JOURNAL_ENTRYID** ([PidTagIpmJournalEntryId](pidtagipmjournalentryid-canonical-property.md))  <br/> |
|Calendar root folder  <br/> |**PR_IPM_APPOINTMENT_ENTRYID** ([PidTagIpmAppointmentEntryId](pidtagipmappointmententryid-canonical-property.md))  <br/> |
|Notes root folder  <br/> |**PR_IPM_NOTE_ENTRYID** ([PidTagIpmNoteEntryId](pidtagipmnoteentryid-canonical-property.md))  <br/> |
|Tasks root folder  <br/> |**PR_IPM_TASK_ENTRYID** ([PidTagIpmTaskEntryId](pidtagipmtaskentryid-canonical-property.md))  <br/> |
   
Before you try to retrieve one of these special entry identifiers, retrieve the **PR\_VALID_FOLDER_MASK** ([PidTagValidFolderMask](pidtagvalidfoldermask-canonical-property.md)) property of the message store. **PR\_VALID_FOLDER_MASK** is a bitmask that identifies which of the special entry identifiers exist. There is one bit for each of the special folders. If the bit is set, it indicates that the corresponding folder is supported and has a valid entry identifier. For example, if the Deleted Items folder exists and has a valid entry identifier, the FOLDER\_IPM_WASTEBASKET_VALID bit will be set in **PR_VALID_FOLDER_MASK**. 
  
## Open the folder where all incoming messages of a particular class are placed
  
1. Call [IMsgStore::GetReceiveFolder](imsgstore-getreceivefolder.md) to retrieve its entry identifier, setting the  _lpszMessageClass_ parameter to point to a character string identifying the message class. For example, if you want to open the Inbox for your IPM subtree, point  _lpszMessageClass_ to IPM. If you want to open the receive folder for IPC messages, set it to point to IPC. 

   If there is no registered receive folder for the message class, **GetReceiveFolder** chooses the receive folder whose associated message class matches the longest possible prefix of the message class passed in. For more information, see [MAPI Receive Folders](mapi-receive-folders.md). 
   
   Note that the **PR_IPM_OUTBOX_ENTRYID** property is used to open the Outbox folder only for IPM messages. If you are opening the Outbox for IPC messages, use instead the entry identifier for its receive folder. Both incoming and outgoing IPC messages are placed in the receive folder. 
    
2. Call one of four **OpenEntry** methods to open the folder and return an interface pointer that you can use to access it. You can call any one of the following methods to open a folder: 
    
   - [IMAPISession::OpenEntry](imapisession-openentry.md)
    
   - [IMSLogon::OpenEntry](imslogon-openentry.md)
    
   - [IMsgStore::OpenEntry](imsgstore-openentry.md)
    
   - [IMAPIContainer::OpenEntry](imapicontainer-openentry.md)
    
   The specific method that you choose depends on the folder to be opened and the objects that are available at the time. Because the **IMAPISession** method can open any folder for any message store in the current profile, call this **OpenEntry** when you do not know anything about the folder to be opened. If you know which message store owns the folder and you have a pointer to the message store, call **IMsgStore::OpenEntry**. 
    
   For example, use the **IMsgStore** method to open a receive folder. If you have a pointer to the message store provider's logon object, call **IMSLogon::OpenEntry**. Because these calls go directly to the message store provider rather than through MAPI, processing is faster. If the folder you are opening is a subfolder of a folder that you already have open, call the open folder's **IMAPIContainer::OpenEntry** method. The **IMAPIContainer** method only opens subfolders of a currently opened folder and is the only method guaranteed to work with short-term entry identifiers. 
    
3. If you want to be able to make changes to the folder to be opened, specify an access level by setting either the MAPI\_BEST\_ACCESS or MAPI\_MODIFY flag in the **OpenEntry** call. These flags are suggestions to the message store provider to grant the highest level of access, for MAPI\_BEST\_ACCESS, or read/write access, for MAPI\_MODIFY, when opening the folder. 

   Because these flags are only suggestions, the folder may or may not be opened with the access level you expect. By retrieving the **PR_ACCESS** ([PidTagAccess](pidtagaccess-canonical-property.md)) property, you can determine the range of operations that can be performed on the open folder. 
    
   However, because many message store providers calculate the value for this property on demand rather than supporting it as a folder property or as a column in their hierarchy table, retrieving it can be time-consuming. An alternate strategy is to attempt whatever operation you need to perform and return an error if necessary.
    
## See also

- [PidTagEntryId Canonical Property](pidtagentryid-canonical-property.md) 
- [IMAPIProp::GetProps](imapiprop-getprops.md)

