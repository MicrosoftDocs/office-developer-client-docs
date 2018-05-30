---
title: "PidTagSendRichInfo Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagSendRichInfo
api_type:
- COM
ms.assetid: e85fc766-197a-484f-b600-68cd28a052a2
description: "Last modified: March 09, 2015"
---

# PidTagSendRichInfo Canonical Property

  
  
**Applies to**: Outlook 
  
Contains TRUE if the recipient can receive all message content, including Rich Text Format (RTF) and Object Linking and Embedding (OLE) objects. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SEND_RICH_INFO  <br/> |
|Identifier:  <br/> |0x3A40  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Address  <br/> |
   
## Remarks

It is recommended that distribution list and messaging user objects expose this property. 
  
This property indicates whether the sender considers the recipient to be MAPI-enabled. 
  
When this property is set to TRUE, the transport and gateway can transmit the full content of the message, including RTF and OLE objects. The transport provider and gateway should use Transport Neutral Encapsulation Format (TNEF) to encapsulate any properties that are not native to all the messaging systems involved. 
  
When this property is set to FALSE, the transport provider and gateway are free to discard message content that their native clients cannot use. For example, when the clients do not support RTF, the transport provider can send only plain text. 
  
When this property is not set, default behavior is determined by the implementation of the transport provider, message transfer agent (MTA), or gateway. Address book providers are not required to support this property. For example, a tightly coupled address book and transport provider can choose to send TNEF but never use RTF. 
  
The client should not assume the transport provider and gateway will use TNEF on their own initiative. Some transport providers and gateways that support TNEF transmit it without regard to the value of this property, but others decline to construct or send TNEF if it is not set to TRUE. 
  
> [!NOTE]
> The setting of this property, and the decisions based on its value, are on a per-recipient basis. 
  
By default, MAPI sets the value to TRUE. A client calling [IAddrBook::CreateOneOff](iaddrbook-createoneoff.md) or a provider calling [IMAPISupport::CreateOneOff](imapisupport-createoneoff.md) can set the **MAPI_SEND_NO_RICH_INFO** bit in the  _ulFlags_ parameter, which causes MAPI to set this property to FALSE. One-offs created by the user interface use the value specified by the creating template. 
  
On calls to the [IAddrBook::ResolveName](iaddrbook-resolvename.md) method when the name cannot be resolved but can be interpreted as an Internet address (SMTP), this property is set to FALSE. To be construed as an Internet address, the display name of the unresolved entry must be in the format X@Y.Z, such as "pete@pinecone.com". 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](http://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for email message objects.
    
[[MS-OXCMAIL]](http://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> from Internet standard email conventions to message objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[PidTagAttachDataObject Canonical Property](pidtagattachdataobject-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

