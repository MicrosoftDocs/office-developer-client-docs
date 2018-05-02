---
title: "IMsgStore  IMAPIProp"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMsgStore
api_type:
- COM
ms.assetid: 20090114-b183-4767-8971-a304a9aa47e6
description: "Last modified: March 09, 2015"
---

# IMsgStore : IMAPIProp

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Provides access to message store information and to messages and folders.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Message store object  <br/> |
|Implemented by:  <br/> |Message store providers  <br/> |
|Called by:  <br/> |Client applications, the MAPI spooler, and MAPI  <br/> |
|Interface identifier:  <br/> |IID_IMsgStore  <br/> |
|Pointer type:  <br/> |LPMDB  <br/> |
|Transaction model:  <br/> |Nontransacted  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[Advise](imsgstore-advise.md) <br/> |Registers to receive notification of specified events that affect the message store.  <br/> |
|[Unadvise](imsgstore-unadvise.md) <br/> |Cancels the sending of notifications previously set up with a call to the **IMsgStore::Advise** method.  <br/> |
|[CompareEntryIDs](imsgstore-compareentryids.md) <br/> |Compares two entry identifiers to determine whether they refer to the same entry in a message store.  <br/> |
|[OpenEntry](imsgstore-openentry.md) <br/> |Opens a folder or message and returns an interface pointer for further access.  <br/> |
|[SetReceiveFolder](imsgstore-setreceivefolder.md) <br/> |Establishes a folder as the destination for incoming messages of a particular message class.  <br/> |
|[GetReceiveFolder](imsgstore-getreceivefolder.md) <br/> |Obtains the folder that was established as the destination for incoming messages of a specified message class or as the default receive folder for the message store.  <br/> |
|[GetReceiveFolderTable](imsgstore-getreceivefoldertable.md) <br/> |Provides access to the receive folder table, a table with information about all of the receive folders for the message store.  <br/> |
|[StoreLogoff](imsgstore-storelogoff.md) <br/> |Enables the orderly logoff of the message store.  <br/> |
|[AbortSubmit](imsgstore-abortsubmit.md) <br/> |Attempts to remove a message from the outgoing queue.  <br/> |
|[GetOutgoingQueue](imsgstore-getoutgoingqueue.md) <br/> |Provides access to the outgoing queue table, a table that has information about all of the messages in the message store's outgoing queue.  <br/> |
|[SetLockState](imsgstore-setlockstate.md) <br/> |Locks or unlocks a message.  <br/> |
|[FinishedMsg](imsgstore-finishedmsg.md) <br/> |Enables the message store provider to perform processing on a sent message.  <br/> |
|[NotifyNewMail](imsgstore-notifynewmail.md) <br/> |Informs the message store that a new message has arrived.  <br/> |
   
|**Required properties**|**Access level**|
|:-----|:-----|
|**PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_OBJECT_TYPE** ( [PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RECORD_KEY** ( [PidTagRecordKey](pidtagrecordkey-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_STORE_ENTRYID** ( [PidTagStoreEntryId](pidtagstoreentryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_STORE_RECORD_KEY** ( [PidTagStoreRecordKey](pidtagstorerecordkey-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_MDB_PROVIDER** ( [PidTagStoreProvider](pidtagstoreprovider-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_STORE_SUPPORT_MASK** ( [PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md))  <br/> |Read-only  <br/> |
   
The following properties are for interpersonal message (IPM) message stores:
  
- **PR_IPM_OUTBOX_ENTRYID** ( [PidTagIpmOutboxEntryId](pidtagipmoutboxentryid-canonical-property.md))
    
- **PR_IPM_SENTMAIL_ENTRYID** ( [PidTagIpmSentMailEntryId](pidtagipmsentmailentryid-canonical-property.md))
    
- **PR_IPM_SUBTREE_ENTRYID** ( [PidTagIpmSubtreeEntryId](pidtagipmsubtreeentryid-canonical-property.md))
    
- **PR_IPM_WASTEBASKET_ENTRYID** ( [PidTagIpmWastebasketEntryId](pidtagipmwastebasketentryid-canonical-property.md))
    
- **PR_MDB_PROVIDER**
    
- **PR_STORE_SUPPORT_MASK**
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)

