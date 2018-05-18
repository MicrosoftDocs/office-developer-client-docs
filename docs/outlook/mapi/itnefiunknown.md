---
title: "ITnef  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ITnef
api_type:
- COM
ms.assetid: eddca896-9497-4425-9904-87ef3cbae298
description: "Last modified: March 09, 2015"
---

# ITnef : IUnknown

  
  
**Applies to**: Outlook 
  
Provides methods for encapsulating MAPI properties that are not supported by a messaging system into binary streams that can be attached to messages. The format used for this encapsulation is the Transport-Neutral Encapsulation Format (TNEF). The target transport provider or MAPI-based client application can then, on receiving a message that includes a TNEF attachment, recover the properties from the attachment.
  
|||
|:-----|:-----|
|Header file:  <br/> |Tnef.h  <br/> |
|Exposed by:  <br/> |TNEF objects  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Transport providers, message store providers, and gateways  <br/> |
|Interface identifier:  <br/> |IID_ITNEF  <br/> |
|Pointer type:  <br/> |LPTNEF  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[AddProps](itnef-addprops.md) <br/> |Enables the calling service provider or gateway to add properties to the encapsulation of a message or an attachment.  <br/> |
|[ExtractProps](itnef-extractprops.md) <br/> |Extracts the properties from a TNEF encapsulation.  <br/> |
|[Finish](itnef-finish.md) <br/> |Finishes processing for all TNEF operations that are queued and waiting.  <br/> |
|[OpenTaggedBody](itnef-opentaggedbody.md) <br/> |Opens a stream interface on the text of an encapsulated message.  <br/> |
|[SetProps](itnef-setprops.md) <br/> |Sets the value of one or more properties for an encapsulated message or attachment without modifying the original message or attachment.  <br/> |
|[EncodeRecips](itnef-encoderecips.md) <br/> |Encodes a view for a message's recipient table in the TNEF data stream for the message.  <br/> |
|[FinishComponent](itnef-finishcomponent.md) <br/> |Processes individual components from a message one at a time into a TNEF stream.  <br/> |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

