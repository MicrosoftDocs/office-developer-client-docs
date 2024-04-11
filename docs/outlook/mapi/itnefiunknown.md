---
title: "ITnef  IUnknown"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- ITnef
api_type:
- COM
ms.assetid: eddca896-9497-4425-9904-87ef3cbae298
description: "Provides methods for encapsulating MAPI properties that are not supported by a messaging system into binary streams that can be attached to messages."
---

# ITnef : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides methods for encapsulating MAPI properties that are not supported by a messaging system into binary streams that can be attached to messages. The format used for this encapsulation is the Transport-Neutral Encapsulation Format (TNEF). The target transport provider or MAPI-based client application can then, on receiving a message that includes a TNEF attachment, recover the properties from the attachment.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Tnef.h  <br/> |
|Exposed by:  <br/> |TNEF objects  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Transport providers, message store providers, and gateways  <br/> |
|Interface identifier:  <br/> |IID_ITNEF  <br/> |
|Pointer type:  <br/> |LPTNEF  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[AddProps](itnef-addprops.md) <br/> |Enables the calling service provider or gateway to add properties to the encapsulation of a message or an attachment. |
|[ExtractProps](itnef-extractprops.md) <br/> |Extracts the properties from a TNEF encapsulation. |
|[Finish](itnef-finish.md) <br/> |Finishes processing for all TNEF operations that are queued and waiting. |
|[OpenTaggedBody](itnef-opentaggedbody.md) <br/> |Opens a stream interface on the text of an encapsulated message. |
|[SetProps](itnef-setprops.md) <br/> |Sets the value of one or more properties for an encapsulated message or attachment without modifying the original message or attachment. |
|[EncodeRecips](itnef-encoderecips.md) <br/> |Encodes a view for a message's recipient table in the TNEF data stream for the message. |
|[FinishComponent](itnef-finishcomponent.md) <br/> |Processes individual components from a message one at a time into a TNEF stream. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

