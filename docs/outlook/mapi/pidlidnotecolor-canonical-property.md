---
title: "PidLidNoteColor Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidNoteColor
api_type:
- COM
ms.assetid: 9d4b8f5f-1789-497c-8010-f83da9ba5966
description: "Last modified: March 09, 2015"
---

# PidLidNoteColor Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the suggested background color of the note. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidNoteColor  <br/> |
|Property set:  <br/> |PSETID_Note  <br/> |
|Long ID (LID):  <br/> |0x00008B00  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Sticky Notes  <br/> |
   
## Remarks

This property must be one of the entries in the following table:
  
|**Value**|**Color**|
|:-----|:-----|
|0x00000000  <br/> |Blue  <br/> |
|0x00000001  <br/> |Green  <br/> |
|0x00000002  <br/> |Pink  <br/> |
|0x00000003  <br/> |Yellow  <br/> |
|0x00000004  <br/> |White  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXONOTE]](http://msdn.microsoft.com/library/6bf4ed7e-316c-4a3c-be27-5ec93e7ab39f%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on notes.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

