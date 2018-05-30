---
title: "PidLidLogStart Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidLogStart
api_type:
- COM
ms.assetid: b8c0c871-51d8-4752-ad4b-607463a9f837
description: "Last modified: March 09, 2015"
---

# PidLidLogStart Canonical Property

  
  
**Applies to**: Outlook 
  
Represents the start date and time for the journal message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidLogStart  <br/> |
|Property set:  <br/> |PSETID_Log  <br/> |
|Long ID (LID):  <br/> |0x00008706  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |Journal  <br/> |
   
## Remarks

The time in Coordinated Universal Time (UTC) when the activity began must be equal to the **dispidCommonStart** ([PidLidCommonStart](pidlidcommonstart-canonical-property.md)) property.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definition and references to related Exchange Server protocol specifications.
    
[[MS-OXOJRNL]](http://msdn.microsoft.com/library/2aa04fd2-0f36-4ce4-9178-c0fc70aa8d43%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for journals.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

