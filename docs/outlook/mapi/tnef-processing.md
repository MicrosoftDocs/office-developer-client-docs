---
title: "TNEF Processing"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 4d324fb3-d917-4502-b3a4-179c479deb79
description: "Last modified: July 05, 2012"
 
 
---

# TNEF Processing

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The following series of actions describe how transports use TNEF methods to process outgoing and incoming messages.
  
 **To send a message that includes a TNEF stream**
  
1. Process the message properties that are supported by the messaging system.
    
2. Mark the message in an implementation specific way so that the receiving transport provider can determine that the message requires TNEF processing. For example, a TNEF transport provider sending to an SMTP messaging system might add a custom header field like "X-CONTAINS-TNEF" to indicate that the message contains TNEF data.
    
3. Obtain a TNEF object and use it to encapsulate the message properties not supported by the messaging system into a TNEF stream.
    
4. Encode the TNEF stream using the messaging system's attachment model. For example, if the underlying attachment model is to uuencode attachments and append them to the message text, then the transport provider must uuencode the TNEF stream into another attachment. The transport provider must also implement a method for recognizing which attachment contains the encoded TNEF stream when it receives a message. The standard way to mark this attachment is to give it an attachment filename of "WINMAIL.DAT". If your transport provider does this, any other TNEF-enabled transport providers that follow this convention will be able to interoperate with it.
    
5. Use [ITnef : IUnknown](itnefiunknown.md) interface methods to insert tags describing the positions of message attachments in the message text. 
    
6. Access the tagged message text through [IStream](http://msdn.microsoft.com/en-us/library/aa380034%28VS.85%29.aspx) methods, and send it to the messaging system. 
    
 **To retrieve encapsulated properties**
  
1. Write the properties supported by the messaging system into a new message, including the tagged message text that contains the encapsulated properties.
    
2. Decode the TNEF stream from the proper attachment.
    
3. Decode any other attachments and write them to new MAPI attachments on a message.
    
4. Open the TNEF stream for decoding using the [OpenTnefStreamEx](opentnefstreamex.md) function. 
    
5. Use the [ITnef::ExtractProps](itnef-extractprops.md) method to decode the TNEF stream and write the encapsulated properties into the new message. Any encoded properties that are duplicates of nonencoded properties will overwrite the nonencoded properties when the encoded properties are decoded. 
    
6. Use the [ITnef::OpenTaggedBody](itnef-opentaggedbody.md) method to parse the message text to recover attachment positions from the tags in the message text. 
    

