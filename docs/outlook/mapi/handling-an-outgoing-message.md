---
title: "Handling an Outgoing Message"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: f40c2e0b-1a35-4901-868f-af6c191c921e
description: "Last modified: July 23, 2011"
 
 
---

# Handling an Outgoing Message

  
  
**Applies to**: Outlook 
  
An outgoing message is a message that can be sent to one or more recipients across one or more messaging systems or be posted to a folder in a message store.
  
 **To create and send an outgoing message**
  
1. Open the default message store. For more information, see [Opening a Message Store](opening-a-message-store.md) and [Opening the Default Message Store](opening-the-default-message-store.md).
    
2. Open the Outbox folder. For more information, see [Opening a Message Store Folder](opening-a-message-store-folder.md).
    
3. Call the Outbox folder's **IMAPIFolder::CreateMessage** method to create the new message. For more information, see [IMAPIFolder::CreateMessage](imapifolder-createmessage.md),
    
4. Create a recipient list with one or more resolved recipients. For more information, see [Creating a Recipient List](creating-a-recipient-list.md).
    
5. Optionally, add a subject. For more information, see [Creating a Message Subject](creating-a-message-subject.md).
    
6. Add the message text. For more information, see [Creating Message Text](creating-message-text.md).
    
7. If the message text is formatted, add rendering information. For more information, see [Adding Rendering Information to Formatted Text](adding-rendering-information-to-formatted-text.md).
    
8. Optionally, add one or more attachments. For more information, see [Creating a Message Attachment](creating-a-message-attachment.md).
    
9. Set other message properties as desired and then save and send the message by calling **IMessage::SubmitMessage**. For more information, see [IMessage::SubmitMessage](imessage-submitmessage.md).
    
10. Delete the sent message if the **PR_DELETE_AFTER_SUBMIT** ([PidTagDeleteAfterSubmit](pidtagdeleteaftersubmit-canonical-property.md)) property is set to TRUE or move it to the folder identified by the **PR_SENTMAIL_ENTRYID** ([PidTagSentMailEntryId](pidtagsentmailentryid-canonical-property.md)) property. For more information, see [Processing a Sent Message](processing-a-sent-message.md).
    
If you want to intermittantly save the message before sending it, call the message's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. For more information, see, [Saving a Message](saving-a-message.md) or [Sending a Message](sending-a-message.md). 
  
## In This Section

[Creating a Recipient List](creating-a-recipient-list.md)
  
> Describes how to create a recipient list.
    
[Creating a Message Subject](creating-a-message-subject.md)
  
> Describes how to create an optional subject for a message.
    
[Creating Message Text](creating-message-text.md)
  
> Describes how to create message text.
    
[Adding Rendering Information to Formatted Text](adding-rendering-information-to-formatted-text.md)
  
> Describes where in formatted text an attachment is to be rendered.
    
[Creating a Message Attachment](creating-a-message-attachment.md)
  
> Describes how to create attachments.
    
[Saving a Message](saving-a-message.md)
  
> Describes how clients save messages.
    
[Sending a Message](sending-a-message.md)
  
> Describes how to send a message.
    
[Processing a Sent Message](processing-a-sent-message.md)
  
> Describes how to sent messages can be processed.
    

