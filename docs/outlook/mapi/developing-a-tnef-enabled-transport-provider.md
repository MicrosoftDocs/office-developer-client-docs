---
title: "Developing a TNEF-Enabled Transport Provider"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 7525eee1-4016-49b8-9509-5ebbe1db819f
description: "Last modified: July 23, 2011"
 
 
---

# Developing a TNEF-Enabled Transport Provider

  
  
**Applies to**: Outlook 
  
To promote interoperability between messaging systems that support different sets of MAPI features, MAPI provides the Transport Neutral Encapsulation Format (TNEF) as a standard way to transfer data. This format encapsulates MAPI properties not supported by an underlying messaging system into a binary stream that can be transferred along with the message when a transport provider sends it. The transport provider that receives the message can then decode the binary stream to retrieve all the properties of the original message and make them available to client applications. The operational model for TNEF is:
  
- Messaging clients submit and receive messages to a TNEF transport as normal.
    
- The transport separates the properties on outgoing messages into two categories: those that the underlying message system supports and those that it does not. The values of the properties that are supported by the underlying messaging system are translated into the required format.
    
- The transport uses the MAPI TNEF methods to encode any unsupported properties into a single data stream. The transport then turns that data stream into a special attachment on the outgoing message, using the underlying messaging system's attachment model, before sending the message.
    
- A TNEF enabled transport that receives such a message does two things. First, it translates the incoming message's properties — the ones supported by the underlying message system — into MAPI properties. Second, if the special attachment is present, it uses the MAPI TNEF methods to retrieve additional MAPI properties from the attachment before delivering the message to a client application.
    
MAPI supplies an implementation of the **ITnef** interface for use by MAPI transport providers when working with TNEF objects. The [OpenTnefStreamEx](opentnefstreamex.md) function is used to create TNEF objects and associate them with a message. TNEF streams are built on top of the OLE **IStream** interface 
  
> [!NOTE]
> You use **OpenTnefStreamEx** to create TNEF objects. The old **OpenTnefStream** function still exists for compatibility with old source code and should not be used in anything new. 
  
The **ITnef** interface provides the following methods: 
  
- [AddProps](itnef-addprops.md)
    
- [EncodeRecips](itnef-encoderecips.md)
    
- [ExtractProps](itnef-extractprops.md)
    
- [Finish](itnef-finish.md)
    
- [FinishComponent](itnef-finishcomponent.md)
    
- [OpenTaggedBody](itnef-opentaggedbody.md)
    
- [SetProps](itnef-setprops.md)
    
The MAPI TNEF implementation model supports:
  
- All MAPI properties without affecting other message properties. In order for MAPI messages to survive transport through a messaging system, all properties that cannot be encoded as properties of the messaging system must be encapsulated. Because it is almost never known at the time a message is sent whether or not a MAPI-compliant client will receive the message, the encapsulation scheme allows a transport provider to encode only those MAPI message properties that the messaging system does not natively support. This means that messages which use TNEF are not "opaque" to messaging systems that are not based on MAPI such as SMTP-based UNIX messaging systems. These systems receive the properties they support in whatever manner is typical for them, and other properties are received as an encoded TNEF data stream. The TNEF transport provider is responsible for differentiating between these two sets of properties and sending the supported set in the proper manner for the messaging system. TNEF makes no assumptions as to the level of support provided by a messaging system. However, in the examples of TNEF usage included in this section, the assumption is made that the messaging system supports at least one single attachment aside from the message. In some cases, the attachment can only be supported through a uuencoded stream and transmitted as part of the message text. Only in very rare circumstances will the messaging system have so little support for message properties that full TNEF encoding of all properties is necessary.
    
- A mechanism for determining whether a TNEF stream on an incoming message belongs to the message, based on the MAPI property **PR_TNEF_CORRELATION_KEY** ([PidTagTnefCorrelationKey](pidtagtnefcorrelationkey-canonical-property.md)). This property should be found both in the TNEF stream and in an appropriate message header. If the property has the same value in both places, or is missing in either place, the TNEF stream is assumed to belong to the message. Otherwise, the TNEF stream is ignored. TNEF enabled transports are responsible for choosing a value for this property on outbound messages and encoding it in an appropriate message header (for example, the Message-ID: header for SMTP messages) and in the TNEF stream.
    

