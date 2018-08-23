---
title: "Writing a Hierarchy Viewer"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 4c939a8c-8148-4add-b181-5a12e6d32309
description: "Last modified: July 23, 2011"
 
 
---

# Writing a Hierarchy Viewer

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A hierarchy viewer is a user interface component that is used for displaying folder and address book container hierarchy tables. Hierarchy viewers can display members of the hierarchy at different levels, expanding and contracting each level on demand.
  
The container property, **PR_DEPTH** ([PidTagDepth](pidtagdepth-canonical-property.md)), controls the level at which a hierarchy member is displayed. Entries that represent top-level address book containers or folders have their **PR_DEPTH** property set to zero. The value of this property is incremented sequentially for entries in sequential levels. That is, when a user selects a top-level container to expand, display all containers with **PR_DEPTH** set to 1. When a user expands one of these subcontainers, display the containers with **PR_DEPTH** set to 2, and so on. 
  
Hierarchy viewers support a different range of depths. You can limit your viewer to only one or two levels or you can support multiple levels, if displaying an expansive hierarchy is a priority. 
  
The address book provides a hierarchy viewer for the top-level containers in the address book. 
  
 **To access the address book hierarchy table**
  
1. Call [IAddrBook::OpenEntry](iaddrbook-openentry.md), passing a null entry identifier, to open the address book's root container.
    
2. Call the root container's [IMAPIContainer::GetHierarchyTable](imapicontainer-gethierarchytable.md) method to access the hierarchy table of the MAPI address book. 
    
 **To access the default message store's hierarchy table**
  
1. Call [IMAPISession::GetMsgStoresTable](imapisession-getmsgstorestable.md) to access the message store table. 
    
2. Build a restriction using the [SPropertyRestriction](spropertyrestriction.md) structure to limit the table to only those rows that have a **PR_DEFAULT_STORE** ([PidTagDefaultStore](pidtagdefaultstore-canonical-property.md)) property set to TRUE. 
    
3. Call [IMAPITable::FindRow](imapitable-findrow.md), passing it the **SPropertyRestriction**, to locate the row representing the default message store. 
    
4. Call [IMAPISession::OpenEntry](imapisession-openentry.md), passing in the **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property from the default message store's row in the message store table.
    
5. Call the message store's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve the **PR_IPM_SUBTREE_ENTRYID** ([PidTagIpmSubtreeEntryId](pidtagipmsubtreeentryid-canonical-property.md)) property.
    
6. Call the message store's [IMsgStore::OpenEntry](imsgstore-openentry.md) method, passing the **PR_IPM_SUBTREE_ENTRYID** property, to open the root folder of the message store's IPM subtree. 
    
7. Call the IPM root folder's [IMAPIContainer::GetHierarchyTable](imapicontainer-gethierarchytable.md) method to access its hierarchy table. 
    

