---
title: "Searching the address book"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 20ff2b63-e4a3-4ba9-bad0-2c1873fb69b5
---

# Searching the address book

**Applies to**: Outlook 2013 | Outlook 2016 
  
MAPI enables address book providers to implement two levels of search functionality:
  
- A basic level that matches a specified name with the **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property of address book entries. This level allows users, for example, to view distribution lists with names beginning with Northwest or locate individual messaging users whose last name is Brown.
    
- An advanced level that matches on properties other than **PR_DISPLAY_NAME**. This level allows users, for example, to further narrow their searches and find messaging users named Brown with a particular address type.
    
Because address book providers can support searching for each of their containers at the basic level, at both levels, or choose not to support it at all, do not expect searching to be implemented as a standard feature. To determine if a particular container supports searches, attempt to establish search criteria in a call to its [IMAPIContainer::SetSearchCriteria](imapicontainer-setsearchcriteria.md) method. If **SetSearchCriteria** returns MAPI_E_NO_SUPPORT, the container does not support searches. 
  
In a container that supports searches, retrieve established criteria by calling [IMAPIContainer::GetSearchCriteria](imapicontainer-getsearchcriteria.md). You can also request that the user be prompted for search criteria before a container's contents table is displayed. To choose this option, set the AB_FIND_ON_OPEN flag of the container's **PR_CONTAINER_FLAGS** ([PidTagContainerFlags](pidtagcontainerflags-canonical-property.md)) property. After the user enters the criteria, it is stored as a restriction and passed to the **SetSearchCriteria** method. Setting AB_FIND_ON_OPEN is particularly useful if you are using an online service or any address book provider that has a slow link to its data. 
  
### To perform a basic search in an address book container
  
1. Call the container's [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md) method to open its contents table. 
    
2. Choose a search technique that meets your needs. The choices include:
    
   - [IMAPITable::FindRow](imapitable-findrow.md) to locate a specific row in the table. 
    
   - [IMAPITable::SortTable](imapitable-sorttable.md) to order rows in the table. 
    
   - [IMAPITable::Restrict](imapitable-restrict.md) to limit the table view. 
    
   - Property restriction using the **PR_ANR** ([PidTagAnr](pidtaganr-canonical-property.md)) property for resolving ambiguous names. Call **IMAPITable::Restrict** to impose this restriction. 
    
   - [IABContainer::ResolveNames](iabcontainer-resolvenames.md) to resolve ambiguous names. 
    
3. Call [IMAPITable::QueryRows](imapitable-queryrows.md) to retrieve any rows that meet your applied search criteria. **QueryRows** can return zero or more matching rows. 
    
The **FindRow**, **SortTable**, and **Restrict** methods are table methods that are available for any table that can be created, either by a client or a service provider. The **PR\_ANR** property restriction and **IABContainer::ResolveNames** method are specific to address book providers and are used for resolving ambiguous names. Ambiguous names are entries in a recipient list that do not have a **PR_ENTRYID** property associated with them. 
  
The **PR\_ANR** restriction invokes an algorithm that separates a character string into words and matches those words with information in the address book using prefix-matching. The information used for the matching depends on the address book provider. All address book providers are required to support the **PR_ANR** restriction for their address book containers. For more information, see [Implementing Name Resolution](implementing-name-resolution.md).
  
**IABContainer::ResolveNames** performs **PR_ANR** restriction processing on multiple names without requiring the container's contents table to be open. Calling **ResolveNames** once to resolve multiple names can be much faster than invoking a **PR\_ANR** restriction multiple times. However, address book providers are not required to support **ResolveNames**.
  

