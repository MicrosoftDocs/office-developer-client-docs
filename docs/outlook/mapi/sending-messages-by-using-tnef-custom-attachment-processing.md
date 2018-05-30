---
title: "Sending Messages by Using TNEF Custom Attachment Processing"
manager: soliver
ms.date: 12/07/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: da318b6f-128a-44b5-8357-a130022030a1
description: "Last modified: December 07, 2015"
 
 
---

# Sending Messages by Using TNEF Custom Attachment Processing

 
  
**Applies to**: Outlook 
  
To customize attachment processing when sending a message:
  
1. Obtain a TNEF object by passing an **IStream** interface and a message into the [OpenTnefStreamEx](opentnefstreamex.md) function. 
    
2. Get a list of all defined properties for the message by calling the [IMAPIProp::GetPropList](imapiprop-getproplist.md) method. 
    
3. Use [IMAPIProp](imapipropiunknown.md) methods to exclude all properties supported by the messaging system. At an appropriate time write those properties to the messaging system in the format required by the messaging system. 
    
4. Call the [ITnef::AddProps](itnef-addprops.md) method to add only the properties on the message — that is, none of the properties on the attachments — by setting the TNEF_PROP_MESSAGE_ONLY flag. 
    
5. Call [ITnef::AddProps](itnef-addprops.md) with these items: the TNEF_PROP_EXCLUDE flag, a property tag array that contains the **PR_ATTACH_DATA_BIN** ([PidTagAttachDataBinary](pidtagattachdatabinary-canonical-property.md)) or **PR_ATTACH_DATA_OBJ** ([PidTagAttachDataObject](pidtagattachdataobject-canonical-property.md)) property, and an attachment identifier that specifies the attachment to be processed.
    
6. Use the [ITnef::SetProps](itnef-setprops.md) method to add the **PR_ATTACH_TRANSPORT_NAME** ([PidTagAttachTransportName](pidtagattachtransportname-canonical-property.md)) property tag with a unique string that identifies the attachment to the messaging system if the attachment has a filename that the messaging system cannot support. For example, multiple attachments with the same original filename, or a filename that is not a valid filename for the messaging system. This string will be used with a key number when writing the attachment tags in the tagged message text to associate an attachment with its data. For more information, see, [TNEF-Tagged Message Text](tnef-tagged-message-text.md).
    
7. Repeat the **AddProps** and **SetProps** calls for each attachment. 
    
8. Call the [ITnef::Finish](itnef-finish.md) method to encode the message into the TNEF stream after all the requested properties are added. 
    
9. Obtain the tagged message text by calling the [ITnef::OpenTaggedBody](itnef-opentaggedbody.md) method. This tagged text is read using methods from the **IStream** interface, encoded using the messaging system's attachment model, and written out to the messaging system. 
    
10. Call the [IUnknown::Release](http://msdn.microsoft.com/library/4b494c6f-f0ee-4c35-ae45-ed956f40dc7a%28Office.15%29.aspx) method to release the [ITnef](itnefiunknown.md) object. 
    
11. Write the remaining attachments to the messaging system through the messaging system's attachment model.
    
Your transport provider should use the previously described procedure to process attachments. If that is not possible, the transport provider should use the following steps for customized attachment processing:
  
1. The transport provider ensures that the **PR_ATTACH_TRANSPORT_NAME** properties of all the attachments contain unique values that are valid attachment identifiers for the messaging system. 
    
2. The transport provider then uses a single call to **ITnef::AddProps** for each attachment, passing in the TNEF_PROP_CONTAINED flag. 
    

