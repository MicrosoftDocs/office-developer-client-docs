---
title: "PidTagAgingPeriod Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAgingPeriod
api_type:
- HeaderDef
ms.assetid: 762020d1-4bc8-d60d-0f66-3929aae24bfb
description: "Last modified: March 09, 2015"
---

# PidTagAgingPeriod Canonical Property

  
  
**Applies to**: Outlook 
  
Represents the number of time units that are used to determine the length of time that an item remains in a folder before the item is archived.
  
## 

|||
|:-----|:-----|
|Associated properties:  <br/> |PR_AGING_PERIOD  <br/> |
|Identifier:  <br/> |0x36EC  <br/> |
|Property type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Miscellaneous  <br/> |
   
## Remarks

The length of time that an item remains in a folder before the item is archived is determined by two properties, **PR_AGING_PERIOD** and **[PR_AGING_GRANULARITY](pidtagaginggranularity-canonical-property.md)**. **PR_AGING_GRANULARITY** represents the time unit in which **PR_AGING_PERIOD** is expressed, when determining this length of time. 
  
The possible values for **PR_AGING_GRANULARITY** can be one of the following. 
  
****

|**Name**|**Description**|
|:-----|:-----|
|**AG_MONTHS** <br/> |**PR_AGING_PERIOD** is defined in number of months.  <br/> |
|**AG_WEEKS** <br/> |**PR_AGING_PERIOD** is defined in number of weeks.  <br/> |
|**AG_DAYS** <br/> |**PR_AGING_PERIOD** is defined in number of days.  <br/> |
   
For example, if a folder archives an item only after the item has been in the folder for two weeks, then **PR_AGING_GRANULARITY** is **AG_WEEKS** and **PR_AGING_PERIOD** is 2. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions.
    
[[MS-OXCFXICS]](http://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Defines the basic data structures that are used in remote operations.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permitted for email message objects.
    
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

