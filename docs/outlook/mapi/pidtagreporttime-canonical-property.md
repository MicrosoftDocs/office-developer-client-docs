---
title: "PidTagReportTime Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagReportTime
api_type:
- COM
ms.assetid: b3646505-a9f0-4a72-8277-b238c909f66f
description: "Last modified: March 09, 2015"
---

# PidTagReportTime Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the date and time when the messaging system generated a report.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_REPORT_TIME  <br/> |
|Identifier:  <br/> |0x0032  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

This property represents a per-recipient property on delivery and nondelivery reports and a per-message property on read and nonread reports. 
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on e-mail messages.
    
[[MS-OXCSPAM]](http://msdn.microsoft.com/library/522f8587-4aed-4cd6-831b-40bd87862189%28Office.15%29.aspx)
  
> Enables the handling of allow/block lists and the determination of junk e-mail messages.
    
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

