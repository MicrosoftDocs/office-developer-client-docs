---
title: "PidLidFileUnderList Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidFileUnderList
api_type:
- COM
ms.assetid: a84d8143-5fe7-4a33-bce4-aebf7a824d5f
description: "Last modified: March 09, 2015"
---

# PidLidFileUnderList Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies a list of possible values for the **dispidFileUnderId** ( [PidLidFileUnderId](pidlidfileunderid-canonical-property.md)) property.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidFileUnderList  <br/> |
|Property set:  <br/> |PSETID_Address  <br/> |
|Long ID (LID):  <br/> |0x00008026  <br/> |
|Data type:  <br/> |PT_MV_LONG  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

Each value in the multi-value property must be one of the allowed values for **dispidFileUnderId** specified in [[MS-OXOCNTC]](http://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx).
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS] ](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](http://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

