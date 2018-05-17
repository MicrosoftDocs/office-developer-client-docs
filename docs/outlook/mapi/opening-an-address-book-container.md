---
title: "Opening an Address Book Container"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 89383b27-618c-4ccb-9e16-f66235c98bfe
description: "Last modified: November 08, 2011"
 
 
---

# Opening an Address Book Container

 
  
**Applies to**: Outlook 
  
After opening the MAPI integrated address book, open one or more address book containers to access the recipients within them.
  
To open the top-level container of the address book, call [IAddrBook::OpenEntry](iaddrbook-openentry.md) with a NULL entry identifier. 
  
Address book containers can be implemented with read-only or read/write access. Read-only containers are used only for browsing. Read/write containers can be modified, allowing clients to create new entries and delete and modify existing entries. All personal address book (PAB) containers are implemented as read/write containers. 
  
To open any lower level container, call **OpenEntry** and specify the entry identifier of the container to be opened. 
  
 **To open the container designated as the PAB**
  
1. Call [IAddrBook::GetPAB](iaddrbook-getpab.md) to retrieve the PAB's entry identifier. 
    
2. Pass this entry identifier to [IAddrBook::OpenEntry](iaddrbook-openentry.md).
    
 **To open a container that is not the PAB**
  
1. Call [IAddrBook::OpenEntry](iaddrbook-openentry.md) with a NULL entry identifier to open the address book's root container. 
    
2. Call the root container's [IMAPIContainer::GetHierarchyTable](imapicontainer-gethierarchytable.md) method to retrieve its hierarchy table — a list of all of the top-level containers in the address book. 
    
3. If the container to be opened is of a specific type:
    
  - Create an **SPropertyRestriction** structure with **PR_DISPLAY_TYPE** ( [PidTagDisplayType](pidtagdisplaytype-canonical-property.md)) for the property tag, the container's type for the property value, and RELOP_EQ for the relation. **PR_DISPLAY_TYPE** can be set to many values, among them: 
    
  - DT_GLOBAL to limit the hierarchy table to containers that belong in the global address list.
    
  - DT_LOCAL to limit the table to containers belonging to a local address book.
    
  - DT_MODIFIABLE to limit the table to containers that can be modified.
    
  - Create an [SPropTagArray](sproptagarray.md) structure that includes **PR_ENTRYID**, **PR_DISPLAY_TYPE**, and any other columns of interest. 
    
  - Call [HrQueryAllRows](hrqueryallrows.md), passing your property restriction and property tag array. **HrQueryAllRows** will return zero or more rows, one row for every container that belongs to the specified type. Be prepared to handle the return of any number of rows. 
    
  - Call **IAddrBook::OpenEntry** with the entry identifier from the **PR_ENTRYID** column of the row that represents the container of interest. 
    
4. If the container to be opened belongs to a specific address book provider:
    
  - Create an [SPropertyRestriction](spropertyrestriction.md) structure with **PR_AB_PROVIDERS** ( [PidTagAbProviders](pidtagabproviders-canonical-property.md)) for the property tag, a provider-specific value for the property value, and RELOP_EQ for the relation. Typically the provider-specific value is a globally unique identifier or GUID. You will find this value published in one of the address book provider's header files. 
    
  - Create an [SPropTagArray](sproptagarray.md) structure that includes **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)), **PR_AB_PROVIDERS**, and any other columns of interest. 
    
  - Call [HrQueryAllRows](hrqueryallrows.md), passing your property restriction and property tag array. **HrQueryAllRows** will return zero rows if the specified address book provider is not in the profile. It can return one or more rows for the provider's top-level containers, depending on how the provider is organized. 
    
  - Call [IAddrBook::OpenEntry](iaddrbook-openentry.md) with the entry identifier from the **PR_ENTRYID** column of the row that represents the container of interest. If the container that you are interested in is not a top-level container, find the top-level container and traverse the hierarchy. 
    

