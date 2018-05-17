---
title: "TNEF Correlation in SMTP Gateways and Transports"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 593f57d7-2891-40d1-a661-478a62d490ff
description: "Last modified: July 23, 2011"
 
 
---

# TNEF Correlation in SMTP Gateways and Transports

  
  
**Applies to**: Outlook 
  
Gateways and transports that connect to internet based systems, those that use SMTP, use the value of the MessageID SMTP header and the **PR_TNEF_CORRELATION_KEY** property to implement TNEF correlation. 
  
The value of the MessageID header of the outbound message should be copied to the **PR_TNEF_CORRELATION_KEY** ( [PidTagTnefCorrelationKey](pidtagtnefcorrelationkey-canonical-property.md)) property and encoded in the [attMAPIProps](attmapiprops.md) attribute of the TNEF stream. Note that **PR_TNEF_CORRELATION_KEY** is a binary property, while the MessageID is a string; the null terminator should be included in the copy and in the comparison. 
  
This technique is used by all Microsoft software that connects MAPI-based messaging systems to the Internet, such as Microsoft Exchange Server. This technique should be used by any SMTP gateways and transports that connect to systems that support MAPI clients in order to maximize interoperability.
  

