---
title: "Encoding a message with TNEF"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 6b86d9a9-6876-4885-ae1e-8571b25b85cc
---

# Encoding a message with TNEF

**Applies to**: Outlook 2013 | Outlook 2016 
  
When a message is submitted, the transport provider can create a file that is used to contain the message during transmission. Next, an [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) interface is wrapped around the file. The transport provider then uses [ITnef](itnefiunknown.md) methods to write the message properties to the stream in a tagged format that enables the properties to be easily decoded by the receiving transport providers. 
  
**To represent an entire message in a single file**
  
1. Obtain a TNEF object by passing an [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) object and a message into the [OpenTnefStreamEx](opentnefstreamex.md) function. 
    
2. Get a list of all defined properties for the message by calling the [IMAPIProp::GetPropList](imapiprop-getproplist.md) method. 
    
3. Use [IMAPIProp](imapipropiunknown.md) methods to exclude all properties supported by the messaging system. At an appropriate time, write those properties to the messaging system in the format required by the messaging system. 
    
4. Call [ITnef::AddProps](itnef-addprops.md) to encode the remaining properties, including all attachments. 
    
5. Call the [ITnef::Finish](itnef-finish.md) method to encode the message into the TNEF stream after all the requested properties are added. 
    
6. Call the [ITnef::OpenTaggedBody](itnef-opentaggedbody.md) method to obtain the tagged message text. This tagged text is written out to the messaging system using methods from the OLE [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) interface. 
    
7. Call the [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28VS.85%29.aspx) method to release the **ITnef** object. 
    
**To process an inbound TNEF message**
  
1. Get a MAPI message object from the MAPI spooler and write message header properties into the new MAPI message.
    
2. Create and initialize an [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) object to contain the TNEF data from the inbound message. 
    
3. Pass the MAPI message and the [IStream](https://msdn.microsoft.com/library/aa380034%28VS.85%29.aspx) object to the [OpenTnefStreamEx](opentnefstreamex.md) function. 
    
4. Decode the information in the TNEF data by calling the [ITnef::ExtractProps](itnef-extractprops.md) method. 
    
   > [!NOTE]
   > Anything decoded by **ExtractProps** will overwrite properties decoded from the incoming message's envelope. That is, extracted TNEF properties will overwrite the existing properties in a message. 
  
5. Process the tagged message text by calling [ITnef::OpenTaggedBody](itnef-opentaggedbody.md) and parse the text to recover attachment positions. 
    
6. Save the message by calling [IMAPIProp::SaveChanges](imapiprop-savechanges.md).
    
7. Release the TNEF object by calling the [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28VS.85%29.aspx) method. 
    

