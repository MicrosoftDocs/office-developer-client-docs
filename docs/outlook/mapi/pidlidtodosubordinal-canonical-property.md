---
title: "PidLidToDoSubOrdinal Canonical Property"
description: Outlines the PidLidToDoSubOrdinal canonical property, which acts as a tie breaker when the dispidToDoOrdinalDate property sorts objects and the result in a tie.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidToDoSubOrdinal
api_type:
- COM
ms.assetid: e3bc15ef-155e-49fd-88e5-64713df9b939
---

# PidLidToDoSubOrdinal Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Acts as a tie breaker when the **dispidToDoOrdinalDate** ([PidLidToDoOrdinalDate](pidlidtodoordinaldate-canonical-property.md)) property sorts objects and the result in a tie.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |dispidToDoSubOrdinal  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x000085A1  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

If used, this property must be sorted lexicographically. The component characters of the string must consist of only the numerals zero through nine. This property should be initially set to "5555555". The length of this property must not exceed 254 characters (excluding the terminating null character).
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOFLAG]](https://msdn.microsoft.com/library/f1e50be4-ed30-4c2a-b5cb-8ff3aaaf9b91%28Office.15%29.aspx)
  
> Specifies the properties and operations related to flagging.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[PidLidToDoOrdinalDate Canonical Property](pidlidtodoordinaldate-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

