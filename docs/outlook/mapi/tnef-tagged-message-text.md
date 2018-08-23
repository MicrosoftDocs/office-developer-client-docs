---
title: "TNEF-Tagged Message Text"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 8c65339e-240c-412d-9b71-69c746468bfb
description: "Last modified: July 23, 2011"
 
 
---

# TNEF-Tagged Message Text

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Tagged message text is used by TNEF to resolve attachment positions in the parent message. This is done by adding a place holder in the message text at the position of the attachment. This place holder, or attachment tag, describes the attachment in such a way that TNEF knows how to resolve the attachment and its position. The tags are formatted as follows:
  
 `[[ <Object Title> : <KeyNum> in <Stream Name> ]] [[ <File Name> : <KeyNum> in <Transport Name> ]]`
  
 **\<Object Title\>** and **\<File Name\>** are variables containing values that are taken from the attachment itself. In cases where these values are not available, the title is defaulted by TNEF based on the attachment type. 
  
The **\<KeyNum\>** variable contains the textual representation of the attachment key assigned to the attachment by TNEF. The base value of the key is passed into the [OpenTnefStreamEx](opentnefstreamex.md) call. The base value must not be zero and should not be the same for every call to **OpenTnefStreamEx**. It should suffice to use pseudo random numbers based on the system time from whatever random number generator your run-time library provides, as long as you guarantee that they are never zero.
  
The **\<Transport Name\>** variable contains either the stream name passed into the [OpenTnefStreamEx](opentnefstreamex.md) call or the value of the **PR_ATTACH_TRANSPORT_NAME** ([PidTagAttachTransportName](pidtagattachtransportname-canonical-property.md)) property.
  
> [!NOTE]
> The **PR_ATTACH_TRANSPORT_NAME** property and the **\<Transport Name\>** variable in a message text tag have nothing to do with the name of the transport provider you are implementing. These items represent the name of an attachment for the transport provider and messaging system. 
  
The message text is tagged when a transport provider asks for a tagged message text by calling the [ITnef::OpenTaggedBody](itnef-opentaggedbody.md) method. When reading from the tagged text stream, TNEF replaces the single character that was in the message text at the index provided in the **PR_RENDERING_POSITION** ([PidTagRenderingPosition](pidtagrenderingposition-canonical-property.md)) property with the appropriate tag. When writing to the tagged text stream, TNEF checks the incoming data for tags, finds the associated attachment, and replaces the tag with a single space character.
  
Note that by using tagged message text, a transport provider can preserve the positioning of attachments regardless of most changes made to the message text by messaging systems.
  

