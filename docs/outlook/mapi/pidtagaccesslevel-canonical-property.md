---
title: "PidTagAccessLevel Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagAccessLevel
api_type:
- HeaderDef
ms.assetid: 8f7119c7-ffc3-47cf-aa1b-b4e56bcc5a24
description: "Indicates the client's access level to the object. This property is read-only for the client."
---

# PidTagAccessLevel Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates the client's access level to the object.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ACCESS_LEVEL  <br/> |
|Identifier:  <br/> |0x0FF7  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Access Control Properties  <br/> |
   
## Remarks

This property is read-only for the client. It must be one of the following values:
  
|**Value**|**Description**|
|:-----|:-----|
|0x00000000  <br/> |Read-Only  <br/> |
|0x00000001  <br/> |Modify  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

