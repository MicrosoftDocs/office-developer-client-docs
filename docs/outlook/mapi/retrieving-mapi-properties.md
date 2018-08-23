---
title: "Retrieving MAPI Properties"
manager: soliver
ms.date: 12/07/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: bd3f9f59-9020-46e6-9560-86a7a0eeca20
description: "Last modified: December 07, 2015"
 
 
---

# Retrieving MAPI Properties

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
When a client or service provider retrieves a property from an object, the object makes available the property's value, type, and identifier. 
  
Clients and service providers can retrieve an object's properties by calling one of the following:
  
[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[IMAPIProp::OpenProperty](imapiprop-openproperty.md)
  
[HrGetOneProp](hrgetoneprop.md)
  
The **GetProps** method is used to retrieve one or more properties that do not need a specialized or alternate interface for access. This implies that the properties available with **GetProps** are small, such as integers and Boolean values. 
  
 **To retrieve multiple properties**
  
1. Allocate an [SPropTagArray](sproptagarray.md) structure large enough to hold the number of properties to be retrieved. 
    
2. Set the **cValues** member of the **SPropTagArray** structure to the number of properties to be retrieved and set each **aulPropTag** member to the identifier and type, if possible, of one of the target properties. If the type is unknown, set it to PT_UNSPECIFIED. If both the type and the identifier are unknown, locate this information by calling [IMAPIProp::GetPropList](imapiprop-getproplist.md). **GetPropList** returns a property tag array with all of the object's supported properties. If only a property name is available, call [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) to access the associated identifier. 
    
3. Call [IMAPIProp::GetProps](imapiprop-getprops.md) to open the property or properties. 
    
The **OpenProperty** method is used to open larger properties that require an alternate interface such as **IStream** or [IMAPITable](imapitableiunknown.md) for access. **OpenProperty** is typically used to open large character string, binary, and object properties and can only open one property at a time. Callers pass in the identifier of the additional interface that is required as one of the input parameters. 
  
Some of the common uses of **OpenProperty** include opening **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)), the property that holds the body of a text-based message, **PR_ATTACH_DATA_OBJ** ([PidTagAttachDataObject](pidtagattachdataobject-canonical-property.md)), the property that holds an OLE object or message attachment, and **PR_CONTAINER_CONTENTS** ([PidTagContainerContents](pidtagcontainercontents-canonical-property.md)), the property that holds a folder or address book container contents table. 
  
Depending on the property, a different interface is requested from **OpenProperty**. **IStream**, an interface that allows property data to be read and written as a stream of bytes, is typically used to access **PR_BODY**. Either [IMessage](imessageimapiprop.md) or **IStream** can be used to access **PR_ATTACH_DATA_OBJ**. Embedded message attachments that are standard messages use **IMessage** whereas messages in the TNEF format use **IStream**. Because **PR_CONTAINER_CONTENTS** is a table object, it is accessed with [IMAPITable](imapitableiunknown.md).
  
 **To retrieve an attachment's PR_ATTACH_DATA_BIN property**
  
1. Call the [OpenStreamOnFile](openstreamonfile.md) function to open a stream for the file. 
    
2. Call the message's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to retrieve the **PR_ATTACH_DATA_BIN** ([PidTagAttachDataBinary](pidtagattachdatabinary-canonical-property.md)) property with the **IStream** interface. Set both the MAPI_MODIFY and MAPI_CREATE flags. 
    
3. Allocate a **STATSTG** structure and pass it in a call to the file stream's **IStream::Stat** method to determine its size. Another way to determine stream size is to call **IStream::Seek** with the flag STREAM_SEEK_END. 
    
4. Call the stream's **IStream::CopyTo** method to copy the data from the file's stream into the attachment stream. 
    
5. When the copy operation is finished, release both streams by calling their **IUnknown::Release** methods. 
    
When **IStream** is used for property access, some service providers automatically send the size of the property back with the stream. Calling **OpenProperty** with the MAPI_DEFERRED_ERRORS flag can delay the opening of the property and the return of the stream size. If **IStream::Stat** is called to retrieve this size after **OpenProperty** with the MAPI_DEFERRED_ERRORS flag set, performance will be impacted because this sequence of calls forces an extra remote procedure call. To avoid the performance hit, clients can call any MAPI method between the calls to **OpenProperty** and to **Stat**.
  
The [HrGetOneProp](hrgetoneprop.md) function, like **OpenProperty**, opens one property at a time. **HrGetOneProp** should only be used when the target object exists on the local machine. When the target object is not locally available, using **HrGetOneProp** repeatedly can result in multiple remote procedure calls and a performance degradation. 
  
Callers that need several properties can either call **HrGetOneProp** or **OpenProperty** in a loop or make one call to **GetProps**. Calling **GetProps** once is more efficient. 
  
> [!NOTE]
> Secure properties are not automatically available with other properties in a **GetProps**, **HrGetOneProp**, or **GetPropList** call. Secure properties must be explicitly requested using their property identifiers. 
  
## See also



[MAPI Property Overview](mapi-property-overview.md)

