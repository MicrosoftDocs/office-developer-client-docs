---
title: "Deleting a Recipient"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: f7495030-e3b8-4c7c-9e19-284ba820e846
description: "Last modified: July 23, 2011"
 
 
---

# Deleting a Recipient

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
 **To remove one or more address book entries from a modifiable container**
  
- Call the [IABContainer::DeleteEntries](iabcontainer-deleteentries.md) method, passing an array of entry identifiers that represent the address book entries to be deleted. **DeleteEntries** can return a warning, MAPI_W_PARTIAL_COMPLETION, to indicate that it couldn't delete one or more of the entries. Test for this return value with the **HR_FAILED** macro and call the container's [IMAPIProp::GetLastError](imapiprop-getlasterror.md) method if more information about the problem is needed. 
    
When you hold a pointer to a deleted entry's [ADRENTRY](adrentry.md) structure in your cache, you will still be able to retrieve properties using its entry identifier. This is because the entry is only marked for deletion. MAPI maintains a level of access to these marked entries by design. 
  

