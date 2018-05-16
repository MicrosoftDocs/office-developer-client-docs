---
title: "PidLidVerbResponse Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidVerbResponse
api_type:
- COM
ms.assetid: 6f3db5ac-f1cb-4c55-ab88-c126dd5f48ee
description: "Last modified: March 09, 2015"
---

# PidLidVerbResponse Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the voting option that a respondent selected.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidVerbResponse  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008524  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

This property is usually set to one of the delimited values that are contained in the **dispidVerbStream** ( [PidLidVerbStream](pidlidverbstream-canonical-property.md)) property on which the respondent votes.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definition and references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for e-mail message objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

