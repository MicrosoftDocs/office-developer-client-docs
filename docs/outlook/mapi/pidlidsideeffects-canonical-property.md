---
title: "PidLidSideEffects Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidSideEffects
api_type:
- COM
ms.assetid: 90d601d9-5eeb-40b6-885d-ccd8a95ae322
description: "Last modified: March 09, 2015"
---

# PidLidSideEffects Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Controls how a message object is handled by the client when acting on end-user input.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidSideEffects  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008510  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Run-time configuration  <br/> |
   
## Remarks

Must be set to a bitwise or zero or more of the following flags.
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|seOpenToDelete  <br/> |0x0001  <br/> |Additional processing is required on the message object when deleting.  <br/> |
|seNoFrame  <br/> |0x0008  <br/> |No UI is associated with the message object.  <br/> |
|seCoerceToInbox  <br/> |0x0010  <br/> |Additional processing is required on the message object when moving or copying to a folder object with a **PR_CONTAINER_CLASS** ([PidTagContainerClass](pidtagcontainerclass-canonical-property.md)) property of "IPF.Note".  <br/> |
|seOpenTocopy  <br/> |0x0020  <br/> |Additional processing is required on the message object when copying to another folder.  <br/> |
|seOpenToMove  <br/> |0x0040  <br/> |Additional processing is required on the message object when moving to another folder.  <br/> |
|seOpenForCtxMenu  <br/> |0x0100  <br/> |Additional processing is required on the message object when displaying verbs to the end-user.  <br/> |
|seCannotUndoDelete  <br/> |0x0400  <br/> |Cannot undo delete operation, must not be set unless "seOpenToDelete" is set.  <br/> |
|seCannotUndoCopy  <br/> |0x0800  <br/> |Cannot undo copy operation, must not be set unless "seOpenTocopy" is set.  <br/> |
|seCannotUndoMove  <br/> |0x1000  <br/> |Cannot undo move operation, must not be set unless "seOpenToMove" is set.  <br/> |
|seHasScript  <br/> |0x2000  <br/> |The message object contains end-user script.  <br/> |
|seOpenToPermDelete  <br/> |0x4000  <br/> |Additional processing is required to permanently delete the message object.  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definition and references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXOCAL]](http://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

