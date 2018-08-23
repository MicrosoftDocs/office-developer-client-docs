---
title: "Encoding Recipient Tables by Using TNEF"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: cd2f595f-4dd0-4704-b670-6857d6c843ca
description: "Last modified: July 23, 2011"
 
 
---

# Encoding Recipient Tables by Using TNEF

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The encoding of a recipient table into the TNEF stream is rarely necessary since most messaging systems support recipient lists directly. In general, the recipient properties are transmitted in the message header. When inclusion of the recipient table is necessary, TNEF can encode the recipient table as a part of its usual processing. This is done during the initial phase of TNEF processing. The transport provider can include the message's recipient table by calling the [ITnef::AddProps](itnef-addprops.md) method with the **PR_MESSAGE_RECIPIENTS** ([PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)) property specified in the inclusion list. TNEF gets the recipient table from the message, queries the column set, and processes every row of the table into the TNEF stream.
  
An alternate method is available if the transport provider needs to modify the recipient table before it is encoded. The transport provider can construct the necessary table and then call the [ITnef::EncodeRecips](itnef-encoderecips.md) method. If NULL is passed in the  _lpRecipTable_ parameter, then the recipient table is taken directly from the message as described for **ITnef::AddProps**.
  

