---
title: "Sending a Reply"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 90dafeae-6b61-40e3-8341-d6a11799d0f2
description: "Last modified: March 09, 2015"
 
 
---

# Sending a Reply

  
  
**Applies to**: Outlook 
  
Client applications typically support two types of replies: one that is sent only to the sender of the original message and one that is sent to all other recipients included in the recipient list of the original message in addition to the sender. This second type of reply is commonly referred to as a reply all message.
  
To send a reply of either type, you implement some of the same tasks that you would when you send an original message. For example, you open the default message store and the outgoing message folder, typically the Outbox, and call the outgoing folder's [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) method to create the reply. Also, you open the folder that holds the original message, typically the Inbox. For information about opening different folders, see [Opening a Message Store Folder](opening-a-message-store-folder.md).
  
The main difference between creating a reply and creating an original message is that with a reply, most of the properties are either based on or copied directly from properties of the original message. Attachments — a message's **PR_MESSAGE_ATTACHMENTS** ( [PidTagMessageAttachments](pidtagmessageattachments-canonical-property.md)) property — are specifically excluded. The recipient list for a reply all message is created from the original message's list with the recipient represented by the **PR_RECEIVED_BY_SEARCH_KEY** ( [PidTagReceivedBySearchKey](pidtagreceivedbysearchkey-canonical-property.md)) property and all blind carbon copy recipients removed. The **PR_RECEIVED_BY_SEARCH_KEY** property represents the current user. 
  
 **To send a reply**
  
1. Open the default message store. For more information, see [Opening the Default Message Store](opening-the-default-message-store.md).
    
2. Open the Outbox folder. For more information, see [Opening a Message Store Folder](opening-a-message-store-folder.md).
    
3. Call the Outbox's [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) method to create the reply. 
    
4. Call the original message's [IMAPIProp::CopyTo](imapiprop-copyto.md) method to copy the following properties to the reply message: 
    
  - **PR_BODY** ( [PidTagBody](pidtagbody-canonical-property.md)) or **PR_RTF_COMPRESSED** ( [PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)), depending on whether or not you support Rich Text Format.
    
  - **PR_MESSAGE_RECIPIENTS** ( [PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)), if the reply will go to the entire recipient list.
    
  - **PR_NORMALIZED_SUBJECT** ( [PidTagNormalizedSubject](pidtagnormalizedsubject-canonical-property.md)).
    
5. Do not include the following properties in your call to **IMAPIProp::CopyTo**:
    
|||
|:-----|:-----|
|**PR_CLIENT_SUBMIT_TIME** <br/> |**PR_MESSAGE_DELIVERY_TIME** <br/> |
|**PR_MESSAGE_DOWNLOAD_TIME** <br/> |**PR_MESSAGE_FLAGS** <br/> |
|**PR_ORIGINATOR_DELIVERY_ REPORT_REQUESTED** <br/> |**PR_RCVD_REPRESENTING** properties  <br/> |
|**PR_READ_RECEIPT_ENTRYID** <br/> |**PR_READ_RECEIPT_REQUESTED** <br/> |
|**PR_RECEIVED_BY** properties  <br/> |**PR_REPLY_RECIPIENT** properties  <br/> |
|**PR_REPORT_ENTRYID** <br/> |**PR_SENDER** properties  <br/> |
|**PR_SENT_REPRESENTING** properties  <br/> |**PR_SENTMAIL_ENTRYID** <br/> |
|**PR_SUBJECT_PREFIX** <br/> | <br/> |
   
1. Add separator text to whichever message body property you support — **PR_BODY**, **PR_HTM**L, or **PR_RTF_COMPRESSED**.
    
2. Call [ScCreateConversationIndex](sccreateconversationindex.md), passing in the value of the original message's **PR_CONVERSATION_INDEX** ( [PidTagConversationIndex](pidtagconversationindex-canonical-property.md)) property.
    
3. Set a prefix for the reply. If you are using the standard "RE:", concatenate these characters onto the beginning of **PR_NORMALIZED_SUBJECT** and set **PR_SUBJECT** ( [PidTagSubject](pidtagsubject-canonical-property.md)) to this new string. Do not set **PR_SUBJECT_PREFIX** ( [PidTagSubjectPrefix](pidtagsubjectprefix-canonical-property.md)). If you are using a nonstandard prefix, such as a string longer than three characters, store it in **PR_SUBJECT_PREFIX**. 
    
4. Set the **PR_SENT_REPRESENTING** properties to the corresponding values in the **PR_RCVD_REPRESENTING** properties. 
    
5. Set each of the entries in **PR_REPLY_RECIPIENT_ENTRIES** ( [PidTagReplyRecipientEntries](pidtagreplyrecipiententries-canonical-property.md)) and **PR_REPLY_RECIPIENT_NAMES** ( [PidTagReplyRecipientNames](pidtagreplyrecipientnames-canonical-property.md)) to the entry identifier and display name of a primary recipient — a recipient whose type is MAPI_TO. Keep these properties synchronized. That is, **PR_REPLY_RECIPIENT_ENTRIES** and **PR_REPLY_RECIPIENT_NAMES** must contain the same number of entries, and an entry at a particular position in one of the properties must correspond to an entry at the same position in the other property. 
    
6. If the reply is being sent only to the sender of the original message, create a single entry recipient list with the recipient represented by the original message's **PR_SENT_REPRESENTING** property. For more information about creating a recipient list, see [Creating a Recipient List](creating-a-recipient-list.md).
    
7. If the reply is a reply all, create a recipient list as follows:
    
1. Call the original message's [IMessage::GetRecipientTable](imessage-getrecipienttable.md) method to access its recipient table. 
    
2. Call [HrQueryAllRows](hrqueryallrows.md) to retrieve all of the rows in the table. Determine if each row represents a primary or carbon copy recipient and should remain in the list or if it represents a blind carbon copy recipient or the user and should be removed from the list. 
    
3. Differentiate between recipient types by looking at the **PR_RECIPIENT_TYPE** ( [PidTagRecipientType](pidtagrecipienttype-canonical-property.md)) column. This column will be set to MAPI_TO for primary recipients, MAPI_CC for carbon copy recipients, and MAPI_BCC for blind carbon copy recipients. 
    
4. Compare the **PR_SEARCH_KEY** ( [PidTagSearchKey](pidtagsearchkey-canonical-property.md)) column with the **PR_RECEIVED_BY_SEARCH_KEY** property of the original message to determine if the row represents the user. 
    
5. Remove unwanted rows from the recipient list by calling [MAPIFreeBuffer](mapifreebuffer.md) to free the memory associated with the corresponding entries in the recipient table's [SRowSet](srowset.md) structure. Set all of the values in the property value array to zero, all of the **cValues** members to zero, and all of the **lpProps** members in each [SRow](srow.md) structure in the **SRowSet** to NULL. 
    
6. Add the sender to the recipient list, as represented by the original message's **PR_SENT_REPRESENTING_NAME** ( [PidTagSentRepresentingName](pidtagsentrepresentingname-canonical-property.md)) and **PR_SENT_REPRESENTING_ENTRYID** ( [PidTagSentRepresentingEntryId](pidtagsentrepresentingentryid-canonical-property.md)) properties. Check that the sender is not duplicated in the list.
    
7. Call the reply message's [IMessage::ModifyRecipients](imessage-modifyrecipients.md) method, setting the  _ulFlags_ parameter to zero, to create a new recipient list for the reply or forwarded message based on the list from the original message. 
    
8. Call the reply's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method to save the message or [IMessage::SubmitMessage](imessage-submitmessage.md) to save and send it. 
    
> [!NOTE]
> Before calling **IMessage::ModifyRecipients** to store changes in the recipient list, you can allow users to make modifications through the message form. Users can add to the list or remove particular members. Allowing users to make changes to a recipient list is an optional client feature. 
  

