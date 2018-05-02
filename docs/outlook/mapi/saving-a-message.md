---
title: "Saving a Message"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 97bff16b-dc7c-4eed-8834-d0c076d83ca3
description: "Last modified: July 23, 2011"
 
 
---

# Saving a Message

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Before a message is saved, clients typically call the message's [IMAPIProp::SetProps](imapiprop-setprops.md) method to set a few properties in addition to the message text properties, attachment properties, **PR_SUBJECT** ( [PidTagSubject](pidtagsubject-canonical-property.md)), and properties associated with the recipient list.
  
Set the **PR_MESSAGE_CLASS** ( [PidTagMessageClass](pidtagmessageclass-canonical-property.md)) property to a character string such as IPM.Note that describes the class of the outgoing message. Although clients should set **PR_MESSAGE_CLASS** on all outgoing messages, a default value is supplied by the message store provider if you do not set it. The default message class for outgoing messages is IPM. 
  
Set the MSGFLAG_UNSENT flag in the **PR_MESSAGE_FLAGS** ( [PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property. If desired, also set the MSGFLAG_READ and MSGFLAG_UNMODIFIED flags. Setting the MSGFLAG_UNMODIFIED allows a message under composition to simulate a delivered message. MSGFLAG_UNMODIFIED can only be set by clients before a message has been saved for the first time. 
  
When you are ready to make a permanent copy of an unsent message, call [IMAPIProp::SaveChanges](imapiprop-savechanges.md) on the message and all of its attachments. If you intend to send the message right away, you do not need to call **SaveChanges**. The call to **SubmitMessage** internally saves the message as part of its processing. 
  
When calling **SaveChanges**, it is a good idea to specify the KEEP_OPEN_READWRITE flag, which allows the message to be modified at a later time. Other settable flags include FORCE_SAVE, which indicates that the message or attachment should be closed after changes are committed, KEEP_OPEN_READONLY, which indicates that no further changes will be made, and the flag to allow the message store provider to batch client requests, MAPI_DEFERRED_ERRORS.
  
It is essential that you call **SaveChanges** for every attachment in the message before you call **SaveChanges** for the message. If you fail to save an attachment, the attachment will not be included with the message when it is sent and it will not appear in the message's attachment table. If you fail to save the message after saving all of the attachments, both the message and the attachments will be lost. 
  
When **SaveChanges** is called, the message store provider updates the following properties: 
  
- **PR_DISPLAY_TO** ( [PidTagDisplayTo](pidtagdisplayto-canonical-property.md)) lists all primary recipients.
    
- **PR_DISPLAY_TO** lists all carbon copy recipients. 
    
- **PR_DISPLAY_BCC** ( [PidTagDisplayBcc](pidtagdisplaybcc-canonical-property.md)) lists all blind carbon copy recipients.
    
- **PR_LAST_MODIFICATION_TIME** ( [PidTagLastModificationTime](pidtaglastmodificationtime-canonical-property.md))
    
- **PR_MESSAGE_FLAGS** sets MSGFLAG_HASATTACH if one or more attachments have been saved and clears MSGFLAG_UNMODIFIED to show the message has changed. 
    
- **PR_MESSAGE_SIZE** ( [PidTagMessageSize](pidtagmessagesize-canonical-property.md)) contains the most current size of the message.
    
- **PR_MESSAGE_ATTACHMENTS** ( [PidTagMessageAttachments](pidtagmessageattachments-canonical-property.md)) provides access to the attachment table.
    
- **PR_MESSAGE_RECIPIENTS** ( [PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)) provides access to the recipient table.
    
Some message properties are typically supplied by clients or service providers when a message is created. If a client neglects to set them, it is up to the message store provider to update them at the time **SaveChanges** is called. For example, if a message's **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) and **PR_RECORD_KEY** ( [PidTagRecordKey](pidtagrecordkey-canonical-property.md)) properties were set when the message was created, they need not be modified at save time. However, message store providers that neglect to set them at message creation must set them the first time that **SaveChanges** is called. 
  
If **SaveChanges** returns MAPI_E_CORRUPT_DATA, assume that the data being saved is now lost. Message store providers that use a client-server model for their implementation might return this value when a network connection is lost or the server is not running. Before returning an error to the user, try to write and save the data a second time by making a call to **SetProps** followed by another call to **SaveChanges**. If the data is cached locally, this should not be a problem. However, if there is no local cache or the second **SaveChanges** call fails, display an error to alert the user to the problem. 
  

