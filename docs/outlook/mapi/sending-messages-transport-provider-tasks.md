---
title: "Sending Messages Transport Provider Tasks"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: bd722f48-b166-4670-8dba-897ac50caf37
description: "Last modified: July 23, 2011"
 
 
---

# Sending Messages: Transport Provider Tasks

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 **To transmit a message, transport providers**
  
- Set the message's **PR_RESPONSIBILITY** ([PidTagResponsibility](pidtagresponsibility-canonical-property.md)) property to TRUE after the transport provider has either sent the message or attempted to send the message. If an attempt to send a message fails, transport providers should call [IMAPISupport::StatusRecips](imapisupport-statusrecips.md) to generate a nondelivery report. If the message is sent successfully and the **PR_ORIGINATOR_DELIVERY_REPORT_REQUESTED** ([PidTagOriginatorDeliveryReportRequested](pidtagoriginatordeliveryreportrequested-canonical-property.md)) property is set to TRUE, create an [ADRLIST](adrlist.md) structure containing the successful recipients, setting the **PR_DELIVER_TIME** ([PidTagDeliverTime](pidtagdelivertime-canonical-property.md)) property for each, and call **StatusRecips** to generate a delivery report. For more information about creating delivery and non-delivery reports, see the following topics: [MAPI Report Messages](mapi-report-messages.md), [Required Report Message Properties](required-report-message-properties.md), [Optional Report Message Properties](optional-report-message-properties.md), and [Sending Message Delivery Reports](sending-message-delivery-reports.md).
    
- Set the message's **PR_SENDER** group of properties to the identity of the user that has logged on. This group includes: **PR_SENDER_ENTRYID** ([PidTagSenderEntryId](pidtagsenderentryid-canonical-property.md)), **PR_SENDER_NAME** ([PidTagSenderName](pidtagsendername-canonical-property.md)), **PR_SENDER_SEARCH_KEY** ([PidTagSenderSearchKey](pidtagsendersearchkey-canonical-property.md)), **PR_SENDER_ADDRTYPE** ([PidTagSenderAddressType](pidtagsenderaddresstype-canonical-property.md)), and **PR_SENDER_EMAIL_ADDRESS** ([PidTagSenderEmailAddress](pidtagsenderemailaddress-canonical-property.md)).
    
- Set the message's **PR_SENT_REPRESENTING** properties, if possible, to either the identity of the user that has logged on or to a valid delegate identity. The **PR_SENT_REPRESENTING** properties are used to implement the sending of messages by one user on behalf of another user. Transport providers that do not support these properties should ignore them on outbound messages. 
    
- Set the message's **PR_CLIENT_SUBMIT_TIME** ([PidTagClientSubmitTime](pidtagclientsubmittime-canonical-property.md)) property to indicate when the client called [IMessage::SubmitMessage](imessage-submitmessage.md).
    
- Set the message's **PR_PROVIDER_SUBMIT_TIME** ([PidTagProviderSubmitTime](pidtagprovidersubmittime-canonical-property.md)) property to indicate the date and time that the message store provider marked the message as having been sent. 
    
When a message is sent to a variety of recipients with several messaging systems, each transmitted copy will have a different sender identity. 
  
The transport provider or tightly coupled message store and transport is also responsible for setting originator and reply-to information. Originator information is stored in the **PR_ORIGINATOR** properties and reply-to information is stored in the PR_REPLY properties. The client can set these properties; however, the transport provider is allowed to ignore and overwrite the client's settings. 
  

