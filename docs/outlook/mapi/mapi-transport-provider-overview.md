---
title: "MAPI Transport Provider Overview"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: b193e819-749e-4642-8afc-dbc47b17b617
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Transport Provider Overview

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Transport providers handle message transmission and reception and implement security, if necessary. They also take care of any necessary preprocessing and postprocessing tasks. There is typically one transport provider for every active messaging system.
  
Client applications communicate with the transport provider through a message store provider. 
  
Transport providers register with MAPI to handle one or more particular types of recipient entries. When a message is ready to be sent, MAPI must determine which transport provider should handle the transmission. Depending on the type of recipient, MAPI can even call upon more than one transport provider. If an unavailable transport provider is the only one that can handle the recipient, the message transmission will be postponed until a connection with that provider can be reestablished.
  
Some messaging systems are secure systems; all potential users are required to enter a set of valid credentials before access is permitted. MAPI prevents unauthorized access to such secure messaging systems by having the transport provider validate credentials at logon time. 
  

