---
title: "Receiving Messages by Using TNEF Custom Attachment Processing"
manager: soliver
ms.date: 12/7/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: bb5082fa-8fe3-46fe-b2de-b6dd1af79ea7
description: "Last modified: December 07, 2015"
 
 
---

# Receiving Messages by Using TNEF Custom Attachment Processing

 **Last modified:** December 07, 2015 
  
 * **Applies to:** Outlook * 
  
To receive a TNEF message with customized attachment processing:
  
1. Import all the transmittable properties — those that the messaging system supports — from the incoming message into a new MAPI message. This includes the message text, which contains the TNEF data stream.
    
2. Identify and decode the special attachment that contains the TNEF stream.
    
3. Extract all the attachments from the incoming message into MAPI attachments on the new MAPI message. The recovered filenames, or other identifying markers on the attachments, should be placed into the **PR_ATTACH_TRANSPORT_NAME** ( [PidTagAttachTransportName](pidtagattachtransportname-canonical-property.md)) property of the new attachments so that the [ITnef::ExtractProps](itnef-extractprops.md) method can later associate the correct attachment with the attachment tags encoded in the message text. 
    
4. Create an OLE **IStream** interface to wrap around the decoded TNEF stream and use that object along with the new MAPI message in a call to the [OpenTnefStreamEx](opentnefstreamex.md) function. 
    
5. Call the **ITnef::ExtractProps** method to recover the nontransmittable properties on the message from the TNEF data stream. 
    
6. Call the [ITnef::OpenTaggedBody](itnef-opentaggedbody.md) method with the MAPI_CREATE and MAPI_MODIFY flags set. This call removes the attachment tags from the message text and converts them into attachment position information in the MAPI message. 
    
7. Deliver the message through the MAPI spooler.
    

