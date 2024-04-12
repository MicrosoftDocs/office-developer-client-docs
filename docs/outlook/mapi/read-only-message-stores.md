---
title: "Read-Only Message Stores"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 752ff2d6-ca64-4507-adf1-4c054c321203
 
 
---

# Read-Only Message Stores

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A read-only message store is one in which neither the MAPI client nor the MAPI spooler can create, modify, or delete the objects in the message store. There are many reasons why you might want to implement a read-only message store. For example, a credit reporting firm could use a read-only store to allow its customers or employees to see but not change individual credit reports. Choosing to make a read-only message store has implications for the structure of the store provider and for the store itself. For example, a read-only message store cannot have an Outbox folder, because then MAPI clients would request that new outgoing messages be created in that folder. Similarly, it is the store provider's responsibility to ensure the integrity of the underlying storage mechanism.
  
There are three flags that can be set in the message store's **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property that support different levels of read-only access. The STORE_READONLY flag indicates that all [IMAPIProp : IUnknown](imapipropiunknown.md) interfaces on objects in the message store are read-only. The STORE_MODIFY_OK flag indicates that existing messages in the message store may be modified, but new folders and messages may not be created. The STORE_CREATE_OK flag indicates that new messages and folders may be created, but indicates nothing about whether existing objects may be modified. 
  
The fact that MAPI clients and the MAPI spooler may not be able to create, modify, or delete objects in the message store does not mean that the contents of the underlying storage mechanism never change. Nor does it mean that your store provider never needs write permission to the underlying storage mechanism. In some circumstances those two conditions may apply, but not in the general case of a read-only message store. The level of access that your store provider requires and whether or not your store provider ever changes data in the underlying storage mechanism depends mainly on the specific nature of your store provider.
  
For example, if you are writing a store provider to give MAPI clients access to a database stored on a CD-ROM device, the underlying storage mechanism cannot change and your store provider can have read-only permission for it. If, however, you are writing a store provider to give MAPI clients read-only access to a public folder database, but the store provider needs to keep track of the read/unread status of messages for each user, the store provider will need to write new data to the underlying storage mechanism. However, in neither example does the store provider ever have to create, modify, or delete folders or messages at the request of MAPI clients or the MAPI spooler.
  
The short list of reasons that a store provider would need to write data to an underlying storage mechanism that is otherwise read-only is as follows:
  
- To store the read/unread status of messages.
    
- To implement read/nonread notifications. 
    
- To store views.
    
- To cache persistent indexes for user-defined folder sort orders.
    
- To store the sort order of a folder's contents (supporting [IMAPIFolder::SaveContentsSort](imapifolder-savecontentssort.md)).
    
- To store search criteria, search state, and results, if the message store provider supports searches (supporting [IMAPIContainer::SetSearchCriteria](imapicontainer-setsearchcriteria.md)).
    
If your message store provider can never write data to the underlying storage mechanism, it will need to implement these features by using a separate storage mechanism outside of the underlying storage mechanism. For example, a read-only message store provider could store the read/unread status of messages in the store in a file on the user's computer. This strategy presents additional difficulties but may be the only feasable way for read-only message store providers to implement some features. For example, keeping the contents of the separate storage mechanism synchronized with the objects in the message store is more difficult than storing the read/unread status directly in the message store itself.
  
Searching presents an additional complication for read-only message store providers. Clients use the folder specified in the message store object's **PR_FINDER_ENTRYID** ([PidTagFinderEntryId](pidtagfinderentryid-canonical-property.md)) property to locate the folder used for search results. Read-only message store providers often cannot install a permanent search-results folder into the message store. In that situation, the message store provider should store an entry identifier in the **PR_FINDER_ENTRYID** property that it can recognize when clients open folders so that it can dynamically create a search-results folder instead of reading one from the underlying storage mechanism. However, because many read-only message store providers create all their folders dynamically, this is usually not too much of a burden. 
  
The fact that your message store provider is read-only is advertised in the store provider object's **PR_STORE_SUPPORT_MASK** property. However, do not count on clients to respect that property; your store provider's code should enforce the read-only status of the underlying storage mechanism. 
  
## See also



[Developing a MAPI Message Store Provider](developing-a-mapi-message-store-provider.md)

