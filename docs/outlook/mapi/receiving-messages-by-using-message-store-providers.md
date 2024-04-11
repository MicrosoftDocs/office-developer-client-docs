---
title: "Receiving Messages by Using Message Store Providers"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 4763951e-ccfd-453e-b99c-5c7d5efb90c2
 
 
---

# Receiving Messages by Using Message Store Providers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Message store providers do not have to support incoming message submissions (that is, support the ability for transport providers and the MAPI spooler to use the message store provider as a delivery point for messages). However, if your message store provider does not support incoming message submissions, it cannot be used as the default message store.
  
To support incoming message submissions, your message store provider must do the following:
  
- Support the [IMsgStore::GetReceiveFolderTable](imsgstore-getreceivefoldertable.md) and [IMsgStore::GetReceiveFolder](imsgstore-getreceivefolder.md) methods so client applications can find incoming messages. 
    
- Support the [IMsgStore::NotifyNewMail](imsgstore-notifynewmail.md) method so that the MAPI spooler can inform the message store provider that a new message has arrived. 
    
- Implement notifications so that clients can register for new message notification. Notifications are optional, but your provider should implement them.
    
The sequence of method calls that occurs when an incoming message is delivered to a message store is as follows:
  
1. The MAPI spooler calls [IMsgStore::OpenEntry](imsgstore-openentry.md) with the Inbox [EntryID](entryid.md) to get an [IMAPIFolder](imapifolderimapicontainer.md) interface. 
    
2. The MAPI spooler calls [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) to get a new message object. 
    
3. The MAPI spooler passes the message object to the transport provider.
    
4. The transport provider fills in the message's properties with data from the underlying messaging system and calls the message object's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. 
    
5. The message store provider uses its notification method to inform registered clients that a new message has arrived.
    
6. The MAPI spooler calls the message store's [IMsgStore::NotifyNewMail](imsgstore-notifynewmail.md) method. 
    
## See also



[Message Store Features](message-store-features.md)

