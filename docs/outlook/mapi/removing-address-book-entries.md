---
title: "Removing address book entries"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 107ebcd7-b612-4139-b676-c3851f15bc74
description: "Last modified: July 23, 2011"
---

# Removing address book entries
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Your container's [IABContainer::DeleteEntries](iabcontainer-deleteentries.md) method is called to remove one or more recipients. **DeleteEntries** has two parameters: an array of entry identifiers representing the recipients to be deleted and a reserved flags value. Deleting a recipient affects the contents table of your container; in addition to deleting the recipient, your container must delete the contents table row that represents the recipient. When the row has been removed from the table, your container must issue a table notification to each registered client. 
  
### To implement IABContainer::DeleteEntries
  
1. Delete each recipient represented by the entry identifier from your container.
    
2. If your container's contents table is open:
    
   - Send an  _fnevTableModified_ notification with the **ulTableEvent** member set to TABLE_ROW_DELETED to registered clients for each deleted contents table row. If your provider uses the notification utility, call [IMAPISupport::Notify](imapisupport-notify.md) to send these notifications. 
    
   - If your provider supports object notifications, also send an  _fnevObjectDeleted_ notification. 
    

