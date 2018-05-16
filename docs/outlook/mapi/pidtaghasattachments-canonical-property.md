---
title: "PidTagHasAttachments Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagHasAttachments
api_type:
- HeaderDef
ms.assetid: fd236d74-2868-46a8-bb3d-17f8365931b6
description: "Last modified: March 09, 2015"
---

# PidTagHasAttachments Canonical Property

  
  
**Applies to**: Outlook 
  
Contains TRUE if a message contains at least one attachment. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_HASATTACH  <br/> |
|Identifier:  <br/> |0x0E1B  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

The message store copies this property from the **MSGFLAG_HASATTACH** flag of the **PR_MESSAGE_FLAGS** ( [PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property. A client application can then use **PR_HASATTACH** to sort on message attachments in a message viewer. 
  
The value this property is updated with the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. 
  
## Related Resources

### Protocol Specifications

[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for e-mail message objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

