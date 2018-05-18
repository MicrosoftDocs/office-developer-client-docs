---
title: "Opening an Attachment"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: c0350698-5304-40cd-903d-279471f3c226
description: "Last modified: July 23, 2011"
 
 
---

# Opening an Attachment

  
  
**Applies to**: Outlook 
  
Opening an attachment involves displaying its data. For example, when a file attachment is opened, the contents of the file are displayed. Whereas messages and folders are opened using their entry identifiers, attachments are opened using their attachment numbers — **PR_ATTACH_NUM** properties. For more information, see **PR_ATTACH_NUM** ([PidTagAttachNumber](pidtagattachnumber-canonical-property.md)). Attachment numbers are available through a message's attachment table.
  
 **To open all attachments in a message**
  
1. Call the message's [IMessage::GetAttachmentTable](imessage-getattachmenttable.md) method to access its attachment table. 
    
2. Call [HrQueryAllRows](hrqueryallrows.md) to retrieve all the rows in the table. 
    
3. For each row: 
    
1. Open the attachment by passing the attachment number represented in the **PR_ATTACH_NUM** column in a call to the message's **IMessage::OpenAttach** method. For more information, see [IMessage::OpenAttach](imessage-openattach.md). **OpenAttach** returns a pointer to an **IAttach** implementation that provides access to attachment properties. 
    
2. Call the attachment's **IMAPIProp::GetProps** method to retrieve its **PR_ATTACH_METHOD** property. For more information, see [IMAPIProp::GetProps](imapiprop-getprops.md) and **PR_ATTACH_METHOD** ([PidTagAttachMethod](pidtagattachmethod-canonical-property.md)).
    
3. If **PR_ATTACH_METHOD** is set to ATTACH_BY_REF_ONLY, call **IMAPIProp::GetProps** to retrieve the **PR_ATTACH_PATHNAME** property. For more information, see **PR_ATTACH_PATHNAME** ([PidTagAttachPathname](pidtagattachpathname-canonical-property.md)).
    
4. If **PR_ATTACH_METHOD** is set to ATTACH_BY_VALUE, call **IMAPIProp::OpenProperty** to open the **PR_ATTACH_DATA_BIN** property with the **IStream** interface. See the sample code following this procedure. For more information, see [IMAPIProp::OpenProperty](imapiprop-openproperty.md) and **PR_ATTACH_DATA_BIN** ([PidTagAttachDataBinary](pidtagattachdatabinary-canonical-property.md)).
    
5. If **PR_ATTACH_METHOD** is set to ATTACH_OLE and the attachment is an OLE 2 object: 
    
1. Call **IMAPIProp::OpenProperty** to open the **PR_ATTACH_DATA_OBJ** property with the **IStreamDocfile** interface. Attempt to use this interface because it is an implementation of **IStream** guaranteed to work with structured storage with the least amount of overhead. For more information, see **PR_ATTACH_DATA_OBJ** ([PidTagAttachDataObject](pidtagattachdataobject-canonical-property.md)).
    
2. If the **OpenProperty** call fails, call it again to retrieve the **PR_ATTACH_DATA_BIN** property with the **IStreamDocfile** interface. 
    
3. If this second **OpenProperty** call fails, try again to call **OpenProperty** to retrieve **PR_ATTACH_DATA_OBJ**. However, rather than specifying **IStreamDocfile**, specify the **IStorage** interface. 
    
4. If **PR_ATTACH_METHOD** is set to ATTACH_EMBEDDED_MSG, it is not unusual for the value of **PR_ATTACH_DATA_OBJ** to contain an error. This is because you and the table implementer have no way to agree on the type of object to return. To retrieve a pointer to the attached message, open the attachment using **IMessage::OpenAttach**. Then access the attachment data by calling its **IMAPIProp::OpenProperty** method. For more information, see [IMessage::OpenAttach](imessage-openattach.md) and [IMAPIProp::OpenProperty](imapiprop-openproperty.md).
    
You can request that an attachment is opened in read/write or read-only mode. Read-only is the default mode, and many message store providers open all attachments in this mode regardless of what clients request. Pass the MAPI_BEST_ACCESS flag to request that the message store provider grant the highest level of access it can and then retrieve the open attachment's **PR_ACCESS_LEVEL** property to determine the level of access that was actually granted. For more information, see **PR_ACCESS_LEVEL** ([PidTagAccessLevel](pidtagaccesslevel-canonical-property.md)).
  
The following example shows how to open the data in an attachment's **PR_ATTACH_DATA_BIN** property. It allocates pointers to two streams: one for the file and one for the attachment. The **OpenStreamOnFile** function opens the file stream in read-only mode. The call to the attachment's **IMAPIProp::OpenProperty** method opens the attachment stream in read/write mode. For more information, see **PR_ATTACH_DATA_BIN**, [OpenStreamOnFile](openstreamonfile.md), and [IMAPIProp::OpenProperty](imapiprop-openproperty.md). The code then copies from the file stream to the attachment stream and releases both streams.
  
```
LPSTREAM pStreamFile, pStreamAtt;
HRESULT hr;
hr = OpenStreamOnFile (MAPIAllocateBuffer, MAPIFreeBuffer,
                       STGM_READ, "myfile.doc", NULL, &amp;pStreamFile);
if (HR_SUCCEEDED(hr))
{
    // Open the destination stream in the attachment object
    hr = pAttach->OpenProperty (PR_ATTACH_DATA_BIN,
                                &amp;IID_IStream,
                                0,
                                MAPI_MODIFY | MAPI_CREATE,
                                (LPUNKNOWN *)&amp;pStreamAtt);
    if (HR_SUCCEEDED(hr))
    {
        STATSTG StatInfo;
        pStreamFile->Stat (&amp;StatInfo, STATFLAG_NONAME);
        hResult = pStreamFile->CopyTo (pStreamAtt, StatInfo.cbSize,
                                       NULL, NULL);
        pStreamAtt->Release();
    }
    pStreamFile->Release();
}
```


