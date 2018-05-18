---
title: "Posting a Message"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: cc3e1546-e58b-413f-82d7-4efeb86b0000
description: "Last modified: July 23, 2011"
 
 
---

# Posting a Message

  
  
**Applies to**: Outlook 
  
Posting a message is similar to sending a message. The main difference is the destination. Rather than being directed to one or more recipients across one or more messaging systems, a posted message remains in a folder in the current message store.
  
 **To post a message**
  
1. Open the destination folder by calling [IMsgStore::OpenEntry](imsgstore-openentry.md). If the destination folder is the Inbox, locate the entry identifier to pass to **OpenEntry** by calling [IMsgStore::GetReceiveFolder](imsgstore-getreceivefolder.md). 
    
2. Call [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) to create the message. 
    
3. Call the message's [IMAPIProp::SetProps](imapiprop-setprops.md) method to set: 
    
  - The MSGFLAG_READ flag in the **PidTagMessageFlags** ( [PR_MESSAGE_FLAGS](pidtagmessageflags-canonical-property.md)) property.
    
  - The **PR_SENDER** properties. 
    
  - The **PR_SENT_REPRESENTING** properties. 
    
  - The **PR_RECEIPT_TIME** ([PidTagReceiptTime](pidtagreceipttime-canonical-property.md)) property.
    
  - The **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) or **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) property.
    
  - The **PR_SUBJECT** ([PidTagSubject](pidtagsubject-canonical-property.md)) property.
    
  - The **PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md)) property.
    
  - Any properties required by the message class.
    
4. Call the message's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method to save the message. 
    
5. If necessary, create an attachment, set its properties, and save it. For more information about adding attachments to messages, see [Creating a Message Attachment](creating-a-message-attachment.md).
    
6. Call **IMessage::SaveChanges** to save the message. At this point it will appear in the contents table of the destination folder. 
    
Notice that you do not create a recipient list. Instead, you set several properties that are normally set by a transport provider for a sent message. 
  
If you want to save a message intermittently before having it appear in the contents table of the visible folder, create it instead in a hidden folder such as the root folder of the IPM subtree and then move it to the target folder. 
  

