---
title: "Required Features for Address Book Containers"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 3e221944-5dc9-4cce-8b47-73af84427aea
description: "Last modified: March 09, 2015"
 
 
---

# Required Features for Address Book Containers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Most address book providers support at least one container, some of them modifiable. Address book containers can supply contents and hierarchy tables, search capabilities, and name resolution. Modifiable containers allow the deletion of entries such as messaging users, distribution lists, or other containers and the addition of entries from entries in other containers or from one-off templates.
  
The following table describes features that are required of address book providers that have containers, modifiable or read-only, and how you implement them.
  
|**Feature**|**How to implement**|
|:-----|:-----|
|Access messaging users  <br/> |Implement the [IABLogon::OpenEntry](iablogon-openentry.md) method. For more information, see [Opening Address Book Entries](opening-address-book-entries.md). |
|Compare messaging users  <br/> |Implement the [IABLogon::CompareEntryIDs](iablogon-compareentryids.md) method. For more information, see [Comparing Address Book Entries](comparing-address-book-entries.md). |
|Create messaging users  <br/> |1. Provide a list of creation templates in a one-off table by supporting the **PR_CREATE_TEMPLATES** ([PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property. For more information, see [Implementing a Container One-Off Table](implementing-a-container-one-off-table.md). 2. Implement the [IABContainer::CreateEntry](iabcontainer-createentry.md) method. For more information, see [Adding Address Book Entries](adding-address-book-entries.md). |
|Copy messaging users  <br/> |Implement the [IABContainer::CopyEntries](iabcontainer-copyentries.md) method. For more information, see [Copying Address Book Entries](copying-address-book-entries.md). |
|Remove messaging users  <br/> |Implement the [IABContainer::DeleteEntries](iabcontainer-deleteentries.md) method. For more information, see [Removing Address Book Entries](removing-address-book-entries.md). |
|Provide summary information about messaging users  <br/> |Support the container property **PR_CONTAINER_CONTENTS** ([PidTagContainerContents](pidtagcontainercontents-canonical-property.md)). For more information, see [Contents Tables](contents-tables.md). |
|Provide detailed information about messaging users  <br/> |Support the **PR_DETAILS_TABLE** ([PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) property on messaging users and distribution lists. For more information, see [Displaying Recipient Information](displaying-recipient-information.md) and [Display Tables](display-tables.md). |
|Provide detailed information about a container  <br/> |Support the **PR_DETAILS_TABLE** property on the container. For more information, see [Displaying Recipient Information](displaying-recipient-information.md) and [Display Tables](display-tables.md). |
|Provide a hierarchical list of containers  <br/> |Support the container property **PR_CONTAINER_HIERARCHY** ([PidTagContainerHierarchy](pidtagcontainerhierarchy-canonical-property.md)). For more information, see [Hierarchy Tables](hierarchy-tables.md). |
|Support messaging user properties  <br/> |Implement the [IMailUser : IMAPIProp](imailuserimapiprop.md) interface. |
|Resolve ambiguous names  <br/> | Support the **PR_ANR** ([PidTagAnr](pidtaganr-canonical-property.md)) property restriction.  Optionally implement the [IABContainer::ResolveNames](iabcontainer-resolvenames.md) method. For more information, see [Implementing Name Resolution](implementing-name-resolution.md). |
   

