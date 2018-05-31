---
title: "Structured Storage in MAPI"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 642a678b-4bf2-4246-85cb-c798de23e36f
description: "Last modified: March 09, 2015"
 
 
---

# Structured Storage in MAPI

  
  
**Applies to**: Outlook 
  
Structured storage refers to the hierarchical organization of storage introduced with COM. In a structured storage environment, storage is organized into two or three types of objects: 
  
- Stream objects
    
- Lock bytes objects
    
- Storage objects
    
Stream and lock bytes are lower-level objects that directly access the data. Stream objects implement the **IStream** interface which defines methods for reading, writing, positioning, and copying bytes of data. Lock bytes objects implement another COM interface, **ILockBytes**, to access data with a byte array. Byte arrays are typically used to provide customized access to underlying storage.
  
Storage objects are layered on top of the stream or lock bytes objects; they can contain one or more of these objects as well as other storage objects. Storage objects implement the **IStorage** interface which defines methods for creating, accessing, and maintaining nested objects. 
  
Because **IStream**, **ILockBytes**, and **IStorage** are COM interfaces rather than MAPI interfaces, their methods return COM error values rather than MAPI values. Clients and service providers calling methods in these interfaces must use the API function **MapStorageSCode** to translate these values into MAPI error values. For more information, see [MapStorageSCode](mapstoragescode.md).
  
Clients and service providers use structured storage for working with properties that are too large to maintain with the **IMAPIProp** methods, typically large string and binary properties. One of the common ways that clients or service providers access them is by specifying **IStream** or **IStorage** as the interface identifier in a call to the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method. For example, clients call **OpenProperty** with **PR_ATTACH_DATA_BIN** as the property tag and IID_IStream as the interface identifier to access a binary attachment in a message. 
  
Clients and service providers can implement their own stream and storage objects or call API functions to access implementations supplied by MAPI or COM. Because the supplied implementations serve most purposes, clients and service providers rarely need to create their own. 
  
When a client calls **OpenProperty** on a MAPI object to access one of its properties through a storage object, the service provider will typically open the storage object in direct mode. However, this is typical rather than required behavior. Clients should assume that all storage objects opened or created by service providers are transacted and require a call to **IStorage::Commit**. They should also remember that changes to storage objects will not be made permanent until they call **IMAPIProp::SaveChanges** after the final **Commit** to save the MAPI object. For more information, see [IMAPIProp::SaveChanges](imapiprop-savechanges.md).
  
MAPI and COM provide several API functions for defining or accessing storage and stream objects. The commonly used functions are described in the following table.
  
**Functions for Accessing Storage and Stream Objects**

|**Function**|**Description**|
|:-----|:-----|
|[HrIStorageFromStream](hristoragefromstream.md) <br/> |Creates a storage object to access a stream or lock bytes object.  <br/> |
|[OpenIMsgOnIStg](openimsgonistg.md) <br/> |Creates a message object to access a storage object.  <br/> |
|[OpenStreamOnFile](openstreamonfile.md) <br/> |Creates a stream object to access a file.  <br/> |
|[WrapCompressedRTFStream](wrapcompressedrtfstream.md) <br/> |Creates a stream object that contains the compressed or uncompressed version of a stream holding the rich text of a message.  <br/> |
   
 **To retrieve the names of the streams in a given substorage**
  
1. Call the substorage's **IStorage::EnumElements** method to get an **IEnumSTATSTG** interface. 
    
2. Call **IEnumSTATSTG::Next** with as many **STATSTG** structures at a time as you can. If you ask for 100 at a time, **Next** will usually return S_FALSE with the contents of  _pceltFetched_ set to the number that were actually retrieved. 
    
3. Check for the **STATSTG** structures that are flagged with STGTY_STREAM. 
    
4. Release the  _pwcsName_ parameter. 
    
 **To create a storage object to access an existing stream or lock bytes object**
  
- Clients call [HrIStorageFromStream](hristoragefromstream.md). 
    
 **To create a message object to access an existing storage object**
  
- Service providers and clients call [OpenIMsgOnIStg](openimsgonistg.md). The message object that is created differs from the message objects typically created by message store providers in that it does not support all of the [IMessage : IMAPIProp](imessageimapiprop.md) interface methods, such as **IMessage::SubmitMessage**. An optional input parameter to **OpenIMsgOnIStg** is a callback function that conforms to the [MSGCALLRELEASE](msgcallrelease.md) prototype. This function is called by the new message object when the message's reference count reaches zero. Implementing a **MSGCALLRELEASE** function can be useful for performing final processing before the new message is completely removed. 
    
[OpenStreamOnFile](openstreamonfile.md) is commonly used for storing file attachments because it creates a stream that reads from and writes to a file. **OpenProperty** with **PR_ATTACH_DATA_BIN** as the property tag creates a stream for storing binary attachment data. 
  
 **To compress or uncompress a stream containing message text in the Rich Text Format**
  
- Clients call [WrapCompressedRTFStream](wrapcompressedrtfstream.md). **WrapCompressedRTFStream** creates a stream that wraps the RTF stream. The wrapper stream does not implement all of the **IStream** methods; the following methods are excluded: **Seek**, **SetSize**, **Revert**, **LockRegion**, **UnlockRegion**, **Stat**, and **Clone**. This is because the stream objects created by **WrapCompressedRTFStream** do not support either **SetSize** or **Stat**, there is not an easy way to either extend or retrieve their size. The best strategy is to pick a reasonable buffer size and read or write in a loop.
    
> [!NOTE]
> COM has a storage object implementation based on a byte array that returns an **IEnumSTATSTG** object from the **EnumElements** method that is problematic. In particular, the **QueryInterface** method does not work correctly. Service providers that implement their own storage objects using the COM implementation should create a thin wrapper for the **IEnumSTATSTG** object that forwards calls on to the underlying **IEnumSTATSTG** methods but implements its own **AddRef**, **Release**, **QueryInterface**, and **Clone** methods. 
  

