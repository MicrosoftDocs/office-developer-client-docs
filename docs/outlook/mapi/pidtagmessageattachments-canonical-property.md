---
title: "PidTagMessageAttachments Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMessageAttachments
api_type:
- HeaderDef
ms.assetid: 85762771-b823-4227-9a7b-75b6ac280b2d
description: "Last modified: March 09, 2015"
---

# PidTagMessageAttachments Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a table of attachments for a message. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MESSAGE_ATTACHMENTS  <br/> |
|Identifier:  <br/> |0x0E13  <br/> |
|Data type:  <br/> |PT_OBJECT  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

This property can be excluded in [IMAPIProp::CopyTo](imapiprop-copyto.md) operations or included in [IMAPIProp::CopyProps](imapiprop-copyprops.md) operations. As a property of type PT_OBJECT, it cannot be successfully retrieved by the [IMAPIProp::GetProps](imapiprop-getprops.md) method. Its contents should be accessed by the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method, requesting the **IID_IMAPITable** interface identifier. Service providers must report it to the [IMAPIProp::GetPropList](imapiprop-getproplist.md) method if it is set, but may optionally report it or not if it is not set. 
  
To retrieve table contents, a client application should call the [IMessage::GetAttachmentTable](imessage-getattachmenttable.md) method. For more information, see [Attachment Tables](attachment-tables.md). 
  
This property can be used for subobject restriction by specifying it in the [SSubRestriction](ssubrestriction.md) structure. This allows the client to limit the view of a container to messages with attachments meeting given criteria. A message qualifies for viewing if at least one row in its attachments table, that is, one attachment, satisfies the subobject restriction. 
  
## Related resources

### Protocol specifications

[[MS-OXCDATA]](https://msdn.microsoft.com/library/1afa0cd9-b1a0-4520-b623-bf15030af5d8%28Office.15%29.aspx)
  
> Defines the basic data structures that are used in remote operations.
    
[[MS-OXCFXICS]](https://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Defines the basic data structures that are used in remote operations.
    
[[MS-OXCICAL]](https://msdn.microsoft.com/library/a685a040-5b69-4c84-b084-795113fb4012%28Office.15%29.aspx)
  
> Converts between IETF RFC2445, RFC2446, and RFC2447, and appointment and meeting objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

