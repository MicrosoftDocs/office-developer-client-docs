---
title: "Receive Folder Tables"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 5ff1a5e3-5b96-4f08-9b9b-aeb14304b23b
 
 
---

# Receive Folder Tables

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A receive folder table contains information for all the folders designated as receive folders for a message store. A receive folder is a folder where incoming messages of a particular message class are placed. Message store providers implement receive folder tables and client applications use them by making a call to the [IMsgStore::GetReceiveFolderTable](imsgstore-getreceivefoldertable.md) method. 
  
The following properties make up the required column set in receive folder tables:
  
 **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) 
  
 **PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md)) 
  
 **PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md)) 
  
## See also



[MAPI Tables](mapi-tables.md)

