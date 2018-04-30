---
title: "TNEF Correlation in X.400 Gateways and Transports"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 0ffa0802-bfdd-4993-b4a3-142e5d15bfb4
description: "Last modified: July 23, 2011"
---

# TNEF Correlation in X.400 Gateways and Transports

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Gateways and transports that connect to X.400-based systems, use the value of the IM_THIS_IPM X.400 attribute and the **attMessageID** TNEF attribute to implement TNEF correlation. 
  
The value of the IM_THIS_IPM attribute of the outbound message is copied to **attMessageID** in the TNEF stream. The IM_THIS_IPM X.400 attribute is typically a string, while the **attMessageID** TNEF attribute is a string of hexadecimal digits representing a binary value. Therefore, each character in the IM_THIS_IPM X.400 attribute, including the terminating null character, must be converted to a 2-character hexadecimal string representing the ASCII value of that character. For instance, if the IM_THIS_IPM X.400 attribute is the following string: 
  
3030322D3030312D305337533A3A3936303631312D313533373030
  
then the value of **attMessageID** would be the following sequence of hexadecimal digits: 
  
33 30 33 30 33 32 32 44
  
33 30 33 30 33 31 32 44
  
33 30 35 33 33 37 35 33
  
33 41 33 41 33 39 33 36
  
33 30 33 36 33 31 33 31
  
32 44 33 31 33 35 33 33
  
33 37 33 30 33 30 00
  
This technique is used by the Microsoft Exchange Server X.400 Connector. This technique should be used by any X.400 gateways and transports that connect to Microsoft Exchange Server in order to maximize interoperability.
  
For greatest compatibility with future as well as present Microsoft software, the IM_THIS_IPM X.400 attribute should also be copied to the **PR_TNEF_CORRELATION_KEY** ( [PidTagTnefCorrelationKey](pidtagtnefcorrelationkey-canonical-property.md)) property. However, since **PR_TNEF_CORRELATION_KEY** is a binary property, no translation into a hexadecimal string is necessary. 
  

