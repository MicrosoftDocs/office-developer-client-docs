---
title: "Sending Message Delivery Reports"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: abb12ec5-f0b7-488a-a75d-446f4be53e96
 
 
---

# Sending Message Delivery Reports

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Some underlying messaging systems support delivery reports and some do not. How the transport provider determines whether message delivery or nondelivery reports can be sent to client applications is an implementation detail specific to individual transport providers. If delivery reports can be sent to client applications, transport providers use the [IMAPISupport::StatusRecips](imapisupport-statusrecips.md) method to notify MAPI of successful or unsuccessful delivery for one or more recipients. MAPI then generates delivery or nondelivery reports corresponding to those recipients. Transport providers can also translate incoming delivery and nondelivery reports that are native to the messaging system into MAPI delivery and nondelivery reports by means of **StatusRecips**.
  

