---
title: "Opening a view descriptor"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 1940feb0-9e0f-4d96-9fb9-b9a35a0aa661
description: "Last modified: July 23, 2011"
---

# Opening a view descriptor
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Many folders can be opened with a normal view, a default view, or any number of personalized views. A view describes how to display the contents of a folder. The normal view is used when there is no alternative view and when you are opening the folder for the first time. When an alternative view does exist, you must use it to open the folder.
  
A view is described in a message known as a view descriptor. View descriptors are typically created as associated messages and can appear in either the common or personal view folders or in any IPM folder.
  
### To open a view descriptor
  
1. Call [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md) to retrieve the associated contents table for the folder. 
    
2. Create a restriction that locates only messages with the message class reserved for view descriptors and call [IMAPITable::Restrict](imapitable-restrict.md) to limit the table and [IMAPITable::QueryRows](imapitable-queryrows.md) to retrieve the appropriate rows, or...
    
   Call the folder's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve its **PR_DEFAULT_VIEW_ENTRYID** ([PidTagDefaultViewEntryId](pidtagdefaultviewentryid-canonical-property.md)) property. **PR_DEFAULT_VIEW_ENTRYID** contains the entry identifier for the message containing the default view descriptor for a folder. This call will succeed if the folder supports the use of the MAPI_ASSOCIATED flag on calls to [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) and [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md).
    
3. Call [IMsgStore::OpenEntry](imsgstore-openentry.md) with the entry identifier of the view descriptor to open it. 
    

