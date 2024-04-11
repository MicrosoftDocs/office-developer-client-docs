---
title: "Supporting Multiple Client Access to Messages in Message Stores"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 31885c64-edb2-4a87-8730-09f163dedd40
 
 
---

# Supporting Multiple Client Access to Messages in Message Stores

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
It is possible for multiple client applications to open a given message simultaneously. Message store providers do not have to follow any particular rules for governing such access. However, if the client applications modify the message and save their changes, the store provider should comply with the following rules:
  
- Allow the first call to the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method to proceed as if it were the only client that has the message open. 
    
- On the subsequent **SaveChanges** calls by other clients, the message store provider should ignore the changes and return MAPI_E_OBJECT_CHANGED. 
    
- Allow client applications to respond to a MAPI_E_OBJECT_CHANGED return code by calling **SaveChanges** again with the FORCE_SAVE flag. If a client application does this, the message store provider should replace the previous changes with the new ones. 
    
Alternatively, the message store provider can detect the conflict and present an interface that enables the user to choose whether to keep the original message, overwrite the original message with the new changes, or save the new changes to another location.
  
## See also



[Implementing Messages in Message Stores](implementing-messages-in-message-stores.md)

