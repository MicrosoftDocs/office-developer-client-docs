---
title: "Validating and Initializing a Message Store"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 74f0a1fe-2a79-4b32-ab88-85a8839a2639
description: "Last modified: July 23, 2011"
 
 
---

# Validating and Initializing a Message Store

  
  
**Applies to**: Outlook 
  
When you open a message store through the [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md) method without setting the MDB_NO_MAIL flag, MAPI creates several folders and assigns them default names and roles. MAPI is responsible for creating these folders to avoid the incompatibilities that would inevitably occur if either clients or message store providers were responsible for the creation. 
  
Sometimes it is necessary to verify that the appropriate folders have been created and that they are valid. The [HrValidateIPMSubtree](hrvalidateipmsubtree.md) function is available for this purpose. If you are validating the default message store, pass the MAPI_FULL_IPM_TREE flag. A more extensive group of folders is created for the default message store. When **HrValidateIPMSubtree** receives the MAPI_FULL_IPM_TREE flag, it checks for the following folders: 
  
- Root folder for the IPM subtree
    
- Deleted Items folder in the IPM root folder
    
- Inbox folder in the IPM root folder
    
- Outbox folder in the IPM root folder
    
- Sent Items folder in the IPM root folder
    
- Folder views in the message store's root folder
    
- Common views in the message store's root folder
    
- Search folder in the message store's root folder
    
If the message store is not the default, you can either set or not set the MAPI_FULL_IPM_TREE flag. When this flag is not set, **HrValidateIPMSubtree** checks for only the root folder for the subtree, the Deleted Items folder, and the root folder for message store search results. 
  
To initialize a message store, store the following properties in memory so that they are readily available:
  
- **PR_VALID_FOLDER_MASK** ( [PidTagValidFolderMask](pidtagvalidfoldermask-canonical-property.md))
    
- **PR_STORE_SUPPORT_MASK** ( [PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md))
    
These properties are bitmasks that describe features of the message store. **PR_VALID_FOLDER_MASK** has one bit set for every special folder that exists in the message store and has an assigned entry identifier that is valid. For more information about accessing these folders and their entry identifiers, see [Opening a Message Store Folder](opening-a-message-store-folder.md). 
  
 **PR_STORE_SUPPORT_MASK** has one bit set for every feature supported in the message store. For example, if a message store supports notification and formatted text, its **PR_STORE_SUPPORT_MASK** will have the STORE_NOTIFY_OK and STORE_RTF_OK bits set. 
  
Other properties that should be stored locally include the entry identifiers for the folders that the **PR_VALID_FOLDER_MASK** property describes as valid. Each of these special folders, except for the Inbox folder, has an entry identifier property associated with it. For example, the entry identifier for the Outbox folder is its **PR_IPM_OUTBOX_ENTRYID** ( [PidTagIpmOutboxEntryId](pidtagipmoutboxentryid-canonical-property.md)) property. Because these folders are the folders that will be opened frequently, it is a good idea to have their entry identifiers readily available.
  

