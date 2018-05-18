---
title: "Supporting Object Access and Comparison"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: aac7c6c5-6896-4824-ba36-81bb292777a9
description: "Last modified: July 23, 2011"
 
 
---

# Supporting Object Access and Comparison

  
  
**Applies to**: Outlook 
  
Service providers can use the [IMAPISupport::OpenEntry](imapisupport-openentry.md) and [IMAPISupport::CompareEntryIDs](imapisupport-compareentryids.md) methods to open and compare objects that belong to their provider or to other providers: 
  
Like [IMAPISession::OpenEntry](imapisession-openentry.md) for clients, providers can use their support object's **OpenEntry** method to access any object as long they know the object's entry identifier. Unlike the session method, the support method requires that you specify a valid entry identifier in the  _lpEntryID_ parameter. It cannot be NULL. 
  
To illustrate how a transport provider might use **IMAPISupport::OpenEntry**, consider the following scenario. The transport provider has received a message formatted in Rich Text Format and does not know whether the target recipient can handle this format. Before delivering the message, the transport provider needs to do the following:
  
1. Call the message's [IMessage::GetRecipientTable](imessage-getrecipienttable.md) method to access the recipient table and the recipient's entry identifier, its **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property.
    
2. Pass the entry identifier to **IMAPISupport::OpenEntry** to open the recipient, typically either a messaging user or distribution list. The  _lpInterface_ parameter should be set to NULL because the provider cannot know ahead of time the object type of the recipient. The support object's **OpenEntry** method calls [IMAPISession::OpenEntry](imapisession-openentry.md) to determine the address book provider responsible for the recipient. The session object then calls the appropriate address book provider's **OpenEntry** method to open the recipient and return an interface pointer to the transport provider. 
    
3. Call the recipient's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve its **PR_SEND_RICH_INFO** ([PidTagSendRichInfo](pidtagsendrichinfo-canonical-property.md)) property. If **PR_SEND_RICH_INFO** is set to TRUE, the recipient can handle formatted text. 
    
If you have opened several objects from other providers, you may need to find out whether two entry identifiers refer to the same object. For example, you may have a short-term entry identifier and a long-term entry identifier and these identifiers may or may not identify the same object. To avoid redundant processing, call the [IMAPISupport::CompareEntryIDs](imapisupport-compareentryids.md) method to compare these entry identifiers. You must use this method for entry identifier comparison because entry identifiers cannot be compared directly. 
  
## See also

#### Concepts

[MAPI Service Providers](mapi-service-providers.md)

