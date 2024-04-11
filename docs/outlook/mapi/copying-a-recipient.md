---
title: "Copying a Recipient"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: b9a41f44-4c7e-4c57-b536-63fb85e4fae6
 
 
---

# Copying a Recipient

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
To copy one or more recipients from one container into another or the same container, first check that the target container is modifiable. Containers that are modifiable set the AB_MODIFIABLE flag in their **PR_CONTAINER_FLAGS** ([PidTagContainerFlags](pidtagcontainerflags-canonical-property.md)) property.
  
To copy one or more entries into a modifiable container, call the destination container's [IABContainer::CopyEntries](iabcontainer-copyentries.md) method. Because copying address book entries can be time-consuming, **CopyEntries** accepts four input parameters: an array of entry identifiers for the entries to be copied, a window handle, a progress indicator, and a bitmask of flags. 
  
The window handle and progress indicator are used by the address book provider to show the status of the operation to the user. If you want to display progress, pass a window handle for the parent window of the progress indicator in the _ulUIParam_ parameter and do not set the AB_NO_DIALOG flag in the _ulFlags_ parameter. If you have your own implementation of a progress indicator, pass a pointer to the implementation in the _lpProgress_ parameter. If not, pass NULL. The address book provider will use the MAPI progress indicator implementation. 
  
The bitmask of flags indicates whether or not you want to display a progress indicator and how duplicate entry checking should be handled. Set the AB_NO_DIALOG flag to suppress a progress indicator. Set the CREATE_CHECK_DUP_LOOSE flag to instruct the address book provider to loosely check for duplicates or the CREATE_CHECK_DUP_STRICT flag for stricter duplicate checking. Set the CREATE_REPLACE flag to have copied entries replace existing entries when the provider determines there are duplicates. 
  
When copying into a personal address book (PAB) container, the provider copies some or all of the properties for each entry. Because MAPI does not establish requirements for providers implementing container copy operations, you cannot make assumptions about the number and type of properties that are copied with an address book entry.
  

