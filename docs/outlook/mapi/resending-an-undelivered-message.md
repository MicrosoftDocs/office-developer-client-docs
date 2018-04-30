---
title: "Resending an Undelivered Message"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 71768db3-a107-47c6-8e6b-775e8d40ac36
description: "Last modified: July 23, 2011"
---

# Resending an Undelivered Message

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
A transport provider sends a non-delivery report (NDR) when it cannot successfully deliver a message that you have submitted. It is up to the client whether or not users can attempt to resend these undelivered messages. If you support resending messages, you can either use a form provided by MAPI or implement your own. The MAPI form displays the names of the failed recipients and the reason for the delivery failure, if possible, and includes a button that, when selected, allows a user to resend the message.
  
When a resent message is received, it should look exactly like the original message. The recipient should be unable to differentiate between a message that was delivered on its first attempt at transmission or a subsequent attempt. Replies on this message should work exactly as if the message had been sent successfully the first time.
  
 **To resend an undelivered message**
  
1. Call [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) to create a new message. 
    
2. Copy all of the properties from the original message, excluding the ** PR_MESSAGE_RECIPIENTS ** ( [PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)) property, and the **PR_SENDER** and **PR_SENT_REPRESENTING** properties. Make the following property modifications: 
    
  - Set **PR_MESSAGE_CLASS** ( [PidTagMessageClass](pidtagmessageclass-canonical-property.md)) to the report's **PR_ORIG_MESSAGE_CLASS ** ( [PidTagOriginalMessageClass](pidtagoriginalmessageclass-canonical-property.md)) property.
    
  - Set the MSGFLAG_RESEND flag in the **PR_MESSAGE_FLAGS** ( [PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property.
    
  - Set **PR_ORIGINAL_ENTRYID** ( [PidTagOriginalEntryId](pidtagoriginalentryid-canonical-property.md)) to the original message's **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) property.
    
  - For each recipient, set MAPI_SUBMITTED in the **PR_RECIPIENT_TYPE** ( [PidTagRecipientType](pidtagrecipienttype-canonical-property.md)) property. 
    
  - Duplicate each failed recipient. Change the **PR_RECIPIENT_TYPE** property for the duplicated recipient to MAPI_P1. Therefore, for each failed recipient there are now two entries in the recipient table: one with **PR_RECIPIENT_TYPE** set to its original value and the other with **PR_RECIPIENT_TYPE** set to MAPI_P1. 
    
3. Call [ScCreateConversationIndex](sccreateconversationindex.md) to set up conversation tracking if desired. 
    
4. Call the new message's [IMessage::ModifyRecipients](imessage-modifyrecipients.md) method to update the recipient list. 
    
5. Call [IMessage::SubmitMessage](imessage-submitmessage.md) to save and send the new message. 
    

