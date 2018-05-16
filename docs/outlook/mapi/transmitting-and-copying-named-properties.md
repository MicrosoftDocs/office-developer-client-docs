---
title: "Transmitting and Copying Named Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 37075cfc-461d-4983-9045-d9f1da6739be
description: "Last modified: July 23, 2011"
 
 
---

# Transmitting and Copying Named Properties

  
  
**Applies to**: Outlook 
  
Whenever a named property is sent, moved, or copied, the name remains constant but the identifier must change to adhere to the mapping of the destination object. The only exception to this rule is when the source and destination have the same mapping signature, making remapping unnecessary.
  
It is the responsibility of the transport provider to remap the names of transmitted named properties to appropriate identifiers that work at the destination. The sending transport provider cannot know what the correct mapping is at the destination; it must transmit the names and rely on the receiving transport provider to map them to identifiers that work. The MAPI implementation of TNEF handles the remapping of named properties for transport providers. Transport providers can either handle the remapping manually or use the TNEF implementation. 
  
A similar remapping of named properties must occur when these properties are copied between message stores. However, because message store providers can retrieve the name to identifier mapping of the destination, they can remap the properties right away and not have to rely on the destination message store. 
  
## See also

#### Concepts

[MAPI Named Properties](mapi-named-properties.md)

