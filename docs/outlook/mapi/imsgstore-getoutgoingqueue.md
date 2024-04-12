---
title: "IMsgStoreGetOutgoingQueue"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgStore.GetOutgoingQueue
api_type:
- COM
ms.assetid: 8316ff89-104d-43fd-902b-476fe567e23b
---

# IMsgStore::GetOutgoingQueue

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides access to the outgoing queue table, a table that has information about all of the messages in the message store's outgoing queue. This method is called only by the MAPI spooler.
  
```cpp
HRESULT GetOutgoingQueue(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lppTable_
  
> [out] A pointer to a pointer to the outgoing queue table.
    
## Return value

S_OK 
  
> The outgoing queue table was successfully returned.
    
## Remarks

The **IMsgStore::GetOutgoingQueue** method provides the MAPI spooler with access to the table that shows the message store's queue of outgoing messages. Typically, messages are placed in the outgoing queue table after their [IMessage::SubmitMessage](imessage-submitmessage.md) method is called. However, because the order of submission affects the order of preprocessing and submission to the transport provider, some messages that have been marked for sending might not appear in the outgoing queue table immediately. 
  
## Notes to implementers

For a list of the properties that must be included as columns in your outgoing queue table, see [Outgoing Queue Tables](outgoing-queue-tables.md). 
  
Because the MAPI spooler is designed to accept messages from a message store in ascending order of submission time, either allow the MAPI spooler to sort the outgoing queue table to match this order or establish it as the default sort order.
  
You must support notifications for the outgoing message queue table, ensuring that the MAPI spooler is notified when the contents of the queue change. 
  
## See also



[IMessage::SubmitMessage](imessage-submitmessage.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)

