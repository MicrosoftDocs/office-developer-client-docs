---
title: "Saving a Message in the Inbox"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 3df04d4e-7e80-4232-aadc-c05c99ab59cb
description: "Last modified: July 23, 2011"
 
 
---

# Saving a Message in the Inbox

  
  
**Applies to**: Outlook 
  
 **To store a message in the Inbox without any recipients**
  
1. Call [IMsgStore::GetReceiveFolder](imsgstore-getreceivefolder.md) to retrieve the entry identifier of the Inbox. 
    
2. Call [IMsgStore::OpenEntry](imsgstore-openentry.md) to open the Inbox and retrieve a pointer to it. 
    
3. Call the Inbox's [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) method to create the message. 
    
4. Call the message's [IMAPIProp::SetProps](imapiprop-setprops.md) method to add the **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)), **PR_HTML** ([PidTagHtml](pidtaghtml-canonical-property.md)), or **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) and **PR_SUBJECT** ([PidTagSubject](pidtagsubject-canonical-property.md)) properties. 
    
5. Create each attachment, set its properties, and save it. For detailed information about adding attachments to messages, see [Creating a Message Attachment](creating-a-message-attachment.md).
    
6. Call **IMessage::SaveChanges** to save the message. At this point it will appear in the contents table of the Inbox. 
    
If you want to save a message intermittantly before having it appear in the contents table of the Inbox, create it instead in a hidden folder such as the root folder of the IPM subtree and then move it to the Inbox. 
  

