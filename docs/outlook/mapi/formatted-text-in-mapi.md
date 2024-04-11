---
title: "Formatted Text in MAPI"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 4d0ff834-253b-4e8c-a5be-6e4745a2a66c
 
 
---

# Formatted Text in MAPI

**Applies to**: Outlook 2013 | Outlook 2016
  
The text of a message can be stored and transmitted using plain text or formatted text. Formatted text enhances the message text by altering its appearance with, for example, one or more fonts, font sizes, or text colors. It is recommended that all clients and whenever possible, all message store providers, support formatted text. Supporting formatted text in messages adds value by improving message readability and making message handling easier and more efficient.
  
Formatted text can be implemented in a variety of ways. The most common way is with the Rich Text Format (RTF). MAPI defines three transmittable properties for holding message text information: **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) for plain text, **PR_HTML** ([PidTagHtml](pidtaghtml-canonical-property.md)) for HTML, and **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) for RTF text that has been compressed. Because the formatted version of a message text can be twice as large as the version without the formatting, the RTF text is compressed before it is transferred with the message and stored in the **PR_RTF_COMPRESSED** property. When it is time to display the message on the screen, it is uncompressed using a utility function provided by MAPI.
  
MAPI defines these two message text properties and mechanisms for conversion between them so that RTF-aware clients can interoperate with clients and messaging systems that do not support formatted text.
  
[Synchronizing Text and Formatting](synchronizing-text-and-formatting.md)
  
> Describes how to keep RTF message text synchronized with the formatting.

[Supporting Formatted Text in Outgoing Messages: Client Responsibilities](supporting-formatted-text-in-outgoing-messages-client-responsibilities.md)
  
> Describes client application responsibilities for supporting formatted text in outgoing messages.

[Supporting Formatted Text in Incoming Messages: Client Responsibilities](supporting-formatted-text-in-incoming-messages-client-responsibilities.md)
  
> Describes client application responsibilities for supporting formatted text in incoming messages.

[Supporting Formatted Text: Message Store Responsibilities](supporting-formatted-text-message-store-responsibilities.md)
  
> Describes message store responsibilities for supporting formatted text.

[Supporting Formatted Text: Rendering Attachments](supporting-formatted-text-rendering-attachments.md)
  
> Describes how to choose where attachments are rendered.

[Supporting Formatted Text: Gateway Responsibilities](supporting-formatted-text-gateway-responsibilities.md)
  
> Describes the gateway responsibilities for outgoing and incoming formatted text messages.
