---
title: "Choosing a form's property set"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 5680fed2-b2e7-4c4b-9ba8-2c497b9c433c
---

# Choosing a form's property set

**Applies to**: Outlook 2013 | Outlook 2016 
  
When you implement your form server, you need to have a property for each piece of information that your message class needs. These properties can be predefined MAPI properties, or they can be custom properties that you define. For more information about working with properties, see [MAPI Property Overview](mapi-property-overview.md).
  
Your form configuration file will contain a list of properties that your form server exposes for client applications to use, but this does not have to be the entire list of properties used by your form server. Client applications typically use the exposed properties to enable users to sort messages in a folder or customize their interfaces in some way.
  
MAPI has a large set of predefined properties that suffice for most applications. However, there will be times when a custom message class needs a property that MAPI does not define. You can use custom properties to extend the MAPI predefined set of properties for whatever special information your form server needs to support.
  
You can use either of the following ways to define custom properties:
  
- Choose a name for the property and use the [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) method to obtain a property tag for it. The [IMAPIProp](imapipropiunknown.md) interface through which you call this method comes from the [IMessage](imessageimapiprop.md) pointer that is passed to the form server when the message is created. Note that the property name must be a wide-character string. 
    
- Define a custom property tag yourself. Custom property tags must be in the range 0x6800 through 0x7BFF. Properties in this range are message-class specific.
    
For more information about defining custom properties, see [Defining New MAPI Properties](defining-new-mapi-properties.md).
  
> [!NOTE]
> Form servers that have a message text often use the **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) property to store it. If your form server uses **PR_RTF_COMPRESSED**, it should also ensure that the **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) property contains a text-only version of the message text, in case the resulting message is read by a client that does not support Rich Text Format (RTF) message text. 
  
## See also

- [Developing MAPI Form Servers](developing-mapi-form-servers.md)

