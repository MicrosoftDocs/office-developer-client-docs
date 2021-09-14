---
title: "MAPI Folders"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 8fac3c92-d2f5-479e-a368-ca82bddd8e30
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Folders

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Folders are MAPI objects that serve as the basic unit of organization for messages. Arranged hierarchically, folders can contain messages and other folders. Folders make it easier to locate and work with messages.
  
Folders implement the [IMAPIFolder](imapifolderimapicontainer.md) interface, which indirectly inherits from the **IUnknown** interface through the [IMAPIContainer](imapicontainerimapiprop.md) and [IMAPIProp](imapipropiunknown.md) interfaces. Clients use **IMAPIFolder** to create, copy, and delete messages and folders, to retrieve and set message status, and to set or clear the read flag for a message. Although message store providers are required to support all the methods in **IMAPIFolder**, some methods introduce a level of complexity that message store providers might want to avoid. MAPI saves message store providers some work by implementing some of the more complex folder functionality in the [IMAPISupport](imapisupportiunknown.md) interface. Rather than implementing their own copy methods, for example, message store providers can call the copy methods in the support object and get the same results. 
  
There are three kinds of folders:
  
- Root folders.
    
- Generic folders.
    
- Search folders.
    
Every message store has at least a root folder. The root folder appears at the top of the hierarchy and contains messages and other folders. Root folders cannot be moved, copied, renamed, or deleted. There is only one root folder for each message store.
  
Most other folders are generic folders. Like root folders, generic folders contain messages and other folders. Unlike root folders, they can be moved, copied, renamed, and deleted. Generic folders can be created in the root folder or other generic folders. When a client creates a generic folder in another folder, the new folder is called a subfolder, or child folder. The folder in which the new folder is placed is referred to as the parent folder of the new folder. Generic folders that have the same parent folder are called sibling folders. Both sibling and non-sibling folders may or may not have unique names, depending on the message store provider. Message store providers that require sibling folders to have unique names return the error value MAPI_E_COLLISION when a client attempts to create two folders with the same name in the same parent. 
  
A search folder contains links to messages that match a set of predefined criteria. Because search folders contain links rather than actual messages, they are in effect read-only. They cannot contain other folders or have messages or folders moved or copied into them. They cannot have new messages created in them; and they themselves cannot be moved, copied, or renamed. When a message is deleted from a search folder, it is actually deleted from the folder that contains the message.
  
Folder type is stored in the **PR_FOLDER_TYPE** ([PidTagFolderType](pidtagfoldertype-canonical-property.md)) property. Every folder has this property set to either FOLDER_GENERIC, FOLDER_ROOT, or FOLDER_SEARCH, depending on its type.
  
Every folder has one entry identifier and one record key. The entry identifier, **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)), is used by clients and service providers to open the folder. The record key, **PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md)), is a binary value that is used to compare the folder with other folders. 
  
A folder has other properties to identify related folders and the message store. The following properties are required:
  
- **PR_PARENT_ENTRYID** ([PidTagParentEntryId](pidtagparententryid-canonical-property.md))
    
- **PR_STORE_ENTRYID** ([PidTagStoreEntryId](pidtagstoreentryid-canonical-property.md))
    
- **PR_STORE_RECORD_KEY** ([PidTagStoreRecordKey](pidtagstorerecordkey-canonical-property.md))
    
Some folders support the **PR_ACCESS** ([PidTagAccess](pidtagaccess-canonical-property.md)) property which describes the type of operations a user can perform. For example, one of the valid settings for **PR_ACCESS** is MAPI_ACCESS_DELETE, which indicates that the folder can be removed. Another setting, MAPI_ACCESS_MODIFY, indicates that the folder should be modifiable. 
  
For a complete list of required folder properties, see the [IMAPIFolder](imapifolderimapicontainer.md) interface. 
  
## See also



[MAPI Application Development](mapi-application-development.md)

