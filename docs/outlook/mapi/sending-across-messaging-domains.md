---
title: "Sending Across Messaging Domains"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 65594253-66cd-486a-aa5b-0bc719f761f0
 
 
---

# Sending Across Messaging Domains

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A messaging domain represents one or more messaging systems that share a common address format. Communication across multiple messaging domains involves translating a message sent in the format of the original messaging domain into the format of the destination messaging domain. Because not all address formats are compatible, a gateway is needed to translate the addressing information from the source format into the destination format. To ensure validity across messaging domains, client applications store important addressing information in MAPI properties. In addition, gateways perform the translation, examining the properties known to need translation and changing them to a format that the destination messaging domain can use.
  
Previously, MAPI allowed this addressing information to be associated with only the users who comprise a message's current recipient list. The properties describing each member of the recipient list underwent the required translation by the gateway to ensure validity across messaging domains. However, some applications require that their messages include addressing information about users that perhaps were recipients in the past, will be recipients in the future, or will never be recipients. For example, routing applications, which send messages in a specified order to a group of users, embed addressing information about these users in the messages. The embedded information typically includes the address and address type of the future recipients, and perhaps also their roles and positions in the routing order, their names, and one or more binary identifiers per recipient.
  
To enable messages to include information about these nonrecipient users, MAPI now includes a strategy for ensuring that this nonrecipient information is also translated correctly across messaging domains. This strategy is based on the concept of gateway-mappable properties.
  

