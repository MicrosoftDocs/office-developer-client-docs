---
title: "IMessage  IMAPIProp"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMessage
api_type:
- COM
ms.assetid: 7e244d40-595e-432c-aa8c-f9f62ca3c138
description: "Last modified: March 09, 2015"
---

# IMessage : IMAPIProp

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Manages messages, attachments, and recipients.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Message object  <br/> |
|Implemented by:  <br/> |Message store providers  <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IMessage  <br/> |
|Pointer type:  <br/> |LPMESSAGE  <br/> |
|Transaction model:  <br/> |Transacted  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[GetAttachmentTable](imessage-getattachmenttable.md) <br/> |Returns the message's attachment table.  <br/> |
|[OpenAttach](imessage-openattach.md) <br/> |Opens an attachment.  <br/> |
|[CreateAttach](imessage-createattach.md) <br/> |Creates a new attachment.  <br/> |
|[DeleteAttach](imessage-deleteattach.md) <br/> |Deletes an attachment.  <br/> |
|[GetRecipientTable](imessage-getrecipienttable.md) <br/> |Returns the message's recipient table.  <br/> |
|[ModifyRecipients](imessage-modifyrecipients.md) <br/> |Adds, deletes, or modifies message recipients.  <br/> |
|[SubmitMessage](imessage-submitmessage.md) <br/> |Saves all changes to the message and marks it as ready for sending.  <br/> |
|[SetReadFlag](imessage-setreadflag.md) <br/> |Sets or clears the MSGFLAG_READ flag in the **PR_MESSAGE_FLAGS** ( [PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property of the message and manages the sending of read reports.  <br/> |
   
The following properties are required on messages at some point during their lifecycle. Most of the read-only properties are set by the message store provider when a client calls a message's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. Other read-only properties are set by the transport provider. 
  
|**Required properties for messages of all classes**|**Access**|
|:-----|:-----|
|**PR_CREATION_TIME** ( [PidTagCreationTime](pidtagcreationtime-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_DISPLAY_BCC** ( [PidTagDisplayBcc](pidtagdisplaybcc-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_DISPLAY_CC** ( [PidTagDisplayCc](pidtagdisplaycc-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_DISPLAY_TO** ( [PidTagDisplayTo](pidtagdisplayto-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_LAST_MODIFICATION_TIME** ( [PidTagLastModificationTime](pidtaglastmodificationtime-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_MESSAGE_ATTACHMENTS** ( [PidTagMessageAttachments](pidtagmessageattachments-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_MESSAGE_CLASS** ( [PidTagMessageClass](pidtagmessageclass-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_MESSAGE_FLAGS** ( [PidTagMessageFlags](pidtagmessageflags-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_MESSAGE_RECIPIENTS** ( [PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_MESSAGE_SIZE** ( [PidTagMessageSize](pidtagmessagesize-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_MESSAGE_CC_ME** ( [PidTagMessageCcMe](pidtagmessageccme-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_MESSAGE_RECIP_ME** ( [PidTagMessageRecipientMe](pidtagmessagerecipientme-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_MESSAGE_TO_ME** ( [PidTagMessageToMe](pidtagmessagetome-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_NORMALIZED_SUBJECT** ( [PidTagNormalizedSubject](pidtagnormalizedsubject-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_ORIGINATOR** properties  <br/> |Read-only  <br/> |
|**PR_PARENT_DISPLAY** ( [PidTagParentDisplay](pidtagparentdisplay-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_PARENT_ENTRYID** ( [PidTagParentEntryId](pidtagparententryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RECEIVED_BY** properties  <br/> |Read-only  <br/> |
|**PR_RECIPIENT_TYPE** ( [PidTagRecipientType](pidtagrecipienttype-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RECORD_KEY** ( [PidTagRecordKey](pidtagrecordkey-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_SEARCH_KEY** ( [PidTagSearchKey](pidtagsearchkey-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_SENDER** properties  <br/> |Read-only  <br/> |
|**PR_STORE_ENTRYID** ( [PidTagStoreEntryId](pidtagstoreentryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_STORE_RECORD_KEY** ( [PidTagStoreRecordKey](pidtagstorerecordkey-canonical-property.md))  <br/> |Read-only  <br/> |
   
The following properties are all read-only to clients, with the exception of **PR_BODY**. Clients construct this property when they process a report.
  
|**Properties for report messages**|
|:-----|
|**PR_BODY** ( [PidTagBody](pidtagbody-canonical-property.md))  <br/> |
|**PR_CONVERSATION_INDEX** ( [PidTagConversationIndex](pidtagconversationindex-canonical-property.md))  <br/> |
|**PR_CONVERSATION_TOPIC** ( [PidTagConversationTopic](pidtagconversationtopic-canonical-property.md))  <br/> |
|**PR_MESSAGE_CLASS** <br/> |
|**PR_MESSAGE_DELIVERY_TIME** ( [PidTagMessageDeliveryTime](pidtagmessagedeliverytime-canonical-property.md))  <br/> |
|**PR_ORIGINAL_DELIVERY_TIME** ( [PidTagOriginalDeliveryTime](pidtagoriginaldeliverytime-canonical-property.md))  <br/> |
|**PR_ORIGINAL_DISPLAY_BCC** ( [PidTagOriginalDisplayBcc](pidtagoriginaldisplaybcc-canonical-property.md))  <br/> |
|**PR_ORIGINAL_DISPLAY_CC** ( [PidTagOriginalDisplayCc](pidtagoriginaldisplaycc-canonical-property.md))  <br/> |
|**PR_ORIGINAL_DISPLAY_TO** ( [PidTagOriginalDisplayTo](pidtagoriginaldisplayto-canonical-property.md))  <br/> |
|**PR_ORIGINAL_SUBJECT** ( [PidTagOriginalSubject](pidtagoriginalsubject-canonical-property.md))  <br/> |
|**PR_ORIGINAL_SUBMIT_TIME** ( [PidTagOriginalSubmitTime](pidtagoriginalsubmittime-canonical-property.md))  <br/> |
|**PR_REPORT_TAG** ( [PidTagReportTag](pidtagreporttag-canonical-property.md))  <br/> |
|**PR_REPORT_TEXT** ( [PidTagReportText](pidtagreporttext-canonical-property.md))  <br/> |
|**PR_REPORT_TIME** ( [PidTagReportTime](pidtagreporttime-canonical-property.md))  <br/> |
|**PR_SEARCH_KEY** <br/> |
|**PR_SENDER** properties  <br/> |
|**PR_SUBJECT** ( [PidTagSubject](pidtagsubject-canonical-property.md))  <br/> |
   
|**Properties for message recipients**|**Access**|**Required or optional**|
|:-----|:-----|:-----|
|**PR_ADDRTYPE** ( [PidTagAddressType](pidtagaddresstype-canonical-property.md))  <br/> |Read-only  <br/> |Required  <br/> |
|**PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |Read/write  <br/> |Required  <br/> |
|**PR_DISPLAY_TYPE** ( [PidTagDisplayType](pidtagdisplaytype-canonical-property.md))  <br/> |Read/write  <br/> |Required  <br/> |
|**PR_EMAIL_ADDRESS** ( [PidTagEmailAddress](pidtagemailaddress-canonical-property.md))  <br/> |Read-only  <br/> |Optional  <br/> |
|**PR_ENTRYID** <br/> |Read-only  <br/> |Required  <br/> |
|**PR_OBJECT_TYPE** ( [PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |Read-only  <br/> |Required  <br/> |
|**PR_SEARCH_KEY** <br/> |Read-only  <br/> |Optional  <br/> |
   

