---
title: "Traversing the Inbox Folder"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 2ad1459f-d59a-4784-94ea-4cad194e6e50
description: "Last modified: July 23, 2011"
 
 
---

# Traversing the Inbox Folder

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 **To cycle through all of the messages in the Inbox**
  
1. Call [IMsgStore::GetReceiveFolder](imsgstore-getreceivefolder.md) to retrieve the entry identifier of the Inbox. 
    
2. Call **IMAPIFolder::OpenEntry** to open the Inbox. 
    
3. Call the Inbox's [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md) method to retrieve the contents table. 
    
4. Call the contents table's [IMAPITable::SetColumns](imapitable-setcolumns.md) method to limit the column set to **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) and any other columns you require. 
    
5. Call [IMAPITable::QueryRows](imapitable-queryrows.md) to retrieve a group of rows. 
    
6. Until there are no longer any rows in the contents table:
    
1. Call [IMsgStore::OpenEntry](imsgstore-openentry.md) to open the message represented by the entry identifier from each row. 
    
2. Assign the  _lppUnk_ parameter to a local **IMessage** interface pointer. 
    
3. Work with the properties of the message.
    
4. Release the pointer pointed to by the  _lppUnk_ parameter. 
    
5. Call [IMAPITable::QueryRows](imapitable-queryrows.md) to retrieve the next group of rows. 
    
7. Release the contents table.
    

