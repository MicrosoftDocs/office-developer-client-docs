---
title: "Displaying a folder contents table"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 14a4c123-776d-4a32-9688-8a4402dd1f53
---

# Displaying a folder contents table

**Applies to**: Outlook 2013 | Outlook 2016 
  
The contents table of a folder contains summary information about all of its messages. Summary information about new incoming messages appears in the contents table of the receive folder for the message class. To make this information available to users, retrieve the table and display the columns and rows as appropriate.
  
**To display a folder contents table**
  
1. Call [IMsgStore::OpenEntry](imsgstore-openentry.md), passing the entry identifier of the folder containing the table.
    
2. Call the folder's [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md) method to open its contents table. 
    
3. Limit your view of the contents table if desired by calling the table's [IMAPITable::SetColumns](imapitable-setcolumns.md) method to specify particular columns. 
    
4. Limit your view of the contents table if desired by calling the table's [IMAPITable::Restrict](imapitable-restrict.md) method to filter particular rows. If, for example, you want to show only messages with a specific message class that have yet to be read: 
    
    1. Create a property restriction in an [SPropertyRestriction](spropertyrestriction.md) structure that matches the **PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md)) property with the desired message class. 
        
    2. Create a bitmask restriction in an [SBitMaskRestriction](sbitmaskrestriction.md) structure that uses **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) as the property tag and the MSGFLAG_UNREAD value as the mask.
        
    3. Create a restriction in an [SAndRestriction](sandrestriction.md) structure that joins the property and bitmask restrictions. 
    
5. Sort the contents table if desired by calling the table's [IMAPITable::SortTable](imapitable-sorttable.md) method. 
    
6. Call [IMAPITable::QueryRows](imapitable-queryrows.md) to retrieve all of the rows from the contents table for processing. 
    

