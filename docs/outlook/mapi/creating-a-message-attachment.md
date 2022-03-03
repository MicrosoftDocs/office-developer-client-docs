---
title: "Creating a message attachment"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 711b6765-7763-41ae-9ff8-61ca6ddd459d
---

# Creating a message attachment
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A message attachment is some additional data, such as a file, another message, or an OLE object, that you can send or save along with a message. Each attachment has a collection of properties that identifies it and describes its type and how it is rendered. Like recipients, message attachments can only be accessed through the message to which they belong. Therefore, for an attachment to be usable, its message must be open.
  
## Create a message attachment
  
1. Call the message's [IMessage::CreateAttach](imessage-createattach.md) method and pass NULL as the interface identifier. **CreateAttach** returns a number that uniquely identifies the new attachment within the message. The attachment number is stored in the **PR_ATTACH_NUM** ([PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) property and is valid only as long as the message containing the attachment is open.
    
2. Call [IMAPIProp::SetProps](imapiprop-setprops.md) to set **PR_ATTACH_METHOD** ([PidTagAttachMethod](pidtagattachmethod-canonical-property.md)) to indicate how to access the attachment. **PR_ATTACH_METHOD** is required. Set it to: 
    
   - ATTACH_BY_VALUE if the attachment is binary data.
    
   - ATTACH_BY_REFERENCE, ATTACH_BY_REF_RESOLVE, or ATTACH_BY_REF_ONLY if the attachment is a file.
    
   - ATTACH_EMBEDDED_MSG if the attachment is a message.
    
   - ATTACH_OLE if the attachment is an OLE object.
    
3. Set the appropriate attachment data property:
    
   - **PR_ATTACH_DATA_BIN** ([PidTagAttachDataBinary](pidtagattachdatabinary-canonical-property.md)) for binary data and OLE 1 objects.
    
   - **PR_ATTACH_PATHNAME** ([PidTagAttachPathname](pidtagattachpathname-canonical-property.md)) for files.
    
   - **PR_ATTACH_DATA_OBJ** ([PidTagAttachDataObject](pidtagattachdataobject-canonical-property.md)) for messages and OLE 2 objects.
    
4. Set **PR_ATTACH_RENDERING** ([PidTagAttachRendering](pidtagattachrendering-canonical-property.md)) to hold the graphic representation of the attachment for file or binary attachments. Do not set it for OLE objects, which store the rendering information internally, or for attached messages. 
    
5. Set **PR_RENDERING_POSITION** ([PidTagRenderingPosition](pidtagrenderingposition-canonical-property.md)) to indicate where the attachment should be displayed. **PR_RENDERING_POSITION** applies only to clients that set the **PR_BODY** property. If you only support **PR_RTF_COMPRESSED**, place the following placeholder information in the compressed stream:
    
   `\objattph`

   To set **PR_RENDERING_POSITION**, assign either a number that represents an ordinal offset in characters, with the first character of **PR_BODY** being 0, if you need to know where in the message the attachment is rendered, or 0xFFFFFFFF, if you do not render attachments within **PR_BODY**.
    
6. Set **PR_ATTACH_FILENAME** ([PidTagAttachFilename](pidtagattachfilename-canonical-property.md)) to indicate the short name of the file for a file attachment and **PR\_ATTACH_LONG_FILENAME** ([PidTagAttachLongFilename](pidtagattachlongfilename-canonical-property.md)) to indicate the name of the file as supported on a platform that handles the long filename format. Both properties are optional. However, if you set **PR_ATTACH_LONG_FILENAME**, also set **PR_ATTACH_FILENAME**. 
    
7. Set **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) to indicate the name for the attachment that can appear in a dialog box. PR_DISPLAY_NAME is optional. 
    
## Set PR_ATTACH_DATA_BIN
  
1. Call [IMAPIProp::OpenProperty](imapiprop-openproperty.md) to open the property with the **IStream** interface. 
    
2. If a file contains the data and it is open or if you need explicit control over buffer size, call **IStream::Write** in a loop to place the data in the stream. 
    
3. Another option is to call **OpenStreamOnFile** to create a stream to access the data file and then call this stream's **IStream::CopyTo** method to copy the data to the stream returned by **OpenProperty**.
    
4. Call the new stream's **IStream::Commit** method. 
    
## Set PR_ATTACH_DATA_OBJ
  
1. Call **IMAPIProp::OpenProperty** to open the property with the **IStreamDocfile** interface to create a stream that works with structured storage. **IStreamDocfile** is implemented by message store providers to give clients a higher-performance way to store and retrieve structured storage. The **IStreamDocfile** interface is the same as **IStream**, but the content of the stream is guaranteed to be formatted as structured storage. If this call succeeds, create the stream with the same steps outlined for setting **PR_ATTACH_DATA_BIN**.
    
2. If **OpenProperty** fails: 
    
   1. Call **OpenProperty** again asking for **IStorage**. 
      
   2. Call **StgOpenStorage** to open the OLE object and return a storage object. 
      
   3. Call the returned storage object's **IStorage::CopyTo** method to copy to the storage object returned from **OpenProperty**.
      
   4. Call the new storage object's **IStorage::Commit** method. 
    
## Set PR_ATTACH_PATHNAME
  
1. Allocate an [SPropValue](spropvalue.md) structure, setting the **ulPropTag** member to **PR_ATTACH_PATHNAME** and the **Value.LPSZ** member to the character string that represents the filename. 
    
2. Call the attachment's [IMAPIProp::SetProps](imapiprop-setprops.md) method. 
    
> [!NOTE]
> If your platform supports long filenames, set both **PR_ATTACH_PATHNAME** and **PR_ATTACH_LONG_PATHNAME**. It might be necessary to make an operating system call to retrieve the short filename. 
  
## See also

- [MAPI Attachments](mapi-attachments.md)

