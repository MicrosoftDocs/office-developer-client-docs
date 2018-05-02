---
title: "Required and Optional Interfaces for Message Store Providers"
manager: soliver
ms.date: 12/7/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: cc62e57e-82a4-4f37-8d1b-7cdf828b951e
description: "Last modified: December 07, 2015"
 
 
---

# Required and Optional Interfaces for Message Store Providers

 **Last modified:** December 07, 2015 
  
 * **Applies to:** Outlook * 
  
MAPI defines a set of interfaces that relate to message store providers. Because of the wide range of features that a message store can choose to implement, some of these interfaces are required and some are not. The following table lists the MAPI interfaces that are related to message store providers, specifies whether the interfaces are required or optional, and describes their purpose.
  
|**Interface**|**Status**|**Description**|
|:-----|:-----|:-----|
|[IMSProvider](imsprovideriunknown.md) <br/> |Required  <br/> |Logs on to and off of a message store.  <br/> |
|[IMSLogon](imslogoniunknown.md) <br/> |Required  <br/> |Opens folders or messages, verifies the message store's identity, and handles notifications.  <br/> |
|[IMsgStore](imsgstoreimapiprop.md) <br/> |Required  <br/> |Opens folders or messages, finds special folders, and handles message submissions.  <br/> |
|[IMAPIFolder](imapifolderimapicontainer.md) <br/> |Required  <br/> |Finds and manipulates messages and subfolders.  <br/> |
|[IMessage](imessageimapiprop.md) <br/> |Required  <br/> |Manipulates attachments and sets some of a message's properties.  <br/> |
|[IMAPITable](imapitableiunknown.md) <br/> |Required  <br/> |Enables other objects to present collections of data to various MAPI components.  <br/> |
|[IMAPIStatus](imapistatusimapiprop.md) <br/> |Required  <br/> |Enables clients to validate the state of a message store and to perform some configuration tasks.  <br/> |
|[IAttach](iattachimapiprop.md) <br/> |Optional  <br/> |Accesses message attachment properties if the store provider supports file attachments.  <br/> |
|**IStorage** <br/> |Optional  <br/> |Manages structured storage objects if the store provider supports OLE object attachments.  <br/> |
|**IStream** <br/> |Optional  <br/> |Enables message and attachment objects to read and write data to stream objects.  <br/> |
|**IStreamDocfile** <br/> |Optional  <br/> |Enables some service providers to open a storage object, such as a compound file in the OLE 2.0 file format.  <br/> |
   
The basic information you need to implement **IMAPIFolder**, **IMessage**, **IMAPIStatus**, and **IMAPITable** is documented in the reference topics for these interfaces. This section contains supplementary information that is more directly related to message store providers. The rest of the MAPI interfaces should be implemented according to the information in this section and in the appropriate reference topics. See the COM and ActiveX Object Services section in the Windows SDK for more information about implementing **IStorage**, **IStream**, and **IStreamDocFile**.
  
## See also

#### Concepts

[Developing a MAPI Message Store Provider](developing-a-mapi-message-store-provider.md)

