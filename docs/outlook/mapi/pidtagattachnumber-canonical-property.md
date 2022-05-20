---
title: "PidTagAttachNumber Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagAttachNumber
api_type:
- HeaderDef
ms.assetid: 507e0f2c-383c-4e2f-917b-159913f7234d
description: "Contains a number that uniquely identifies the attachment within its parent message. Message stores generate and maintain this property."
---

# PidTagAttachNumber Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a number that uniquely identifies the attachment within its parent message. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_NUM  <br/> |
|Identifier:  <br/> |0x0E21  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

Message stores generate and maintain this property. The attachment number is the secondary sort key, after the rendering position, in the attachment table. 
  
 **PR_ATTACH_NUM** is used to open the attachment with the [IMessage::OpenAttach](imessage-openattach.md) method. Within a client application's session, the **PR_ATTACH_NUM** property of a message attachment remains constant as long as the attachment table is open. 
  
The message store propagates changes to the table using the **IMessage::CreateAttach** and **IMessage::DeleteAttach** methods. At its option the message store can generate table notifications on open attachment tables so that clients can resynchronize to those changes. 
  
## Related resources

### Protocol specifications

[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
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

