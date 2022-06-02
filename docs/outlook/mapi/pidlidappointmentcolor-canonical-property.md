---
title: "PidLidAppointmentColor Canonical Property"
description: "PidLidAppointmentColor Canonical Property specifies the color to use when displaying the calendar."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidAppointmentColor
api_type:
- COM
ms.assetid: 91147e85-f440-4463-850b-efc9bdbd36d1
---

# PidLidAppointmentColor Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the color to use when displaying the calendar.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidApptColor  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x00008214  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Calendar  <br/> |
   
## Remarks

This property specifies the color to use when displaying the calendar. A client or server should set this value for backward compatibility with older clients. It may instead display the calendar based on the value of the **Keywords** ([PidNameKeywords](pidnamekeywords-canonical-property.md)) property as specified in [[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx). When set, the value must be one of the following.
  
|**Value**|**Color**|
|:-----|:-----|
|0x00000000  <br/> |None  <br/> |
|0x00000001  <br/> |Red  <br/> |
|0x00000002  <br/> |Blue  <br/> |
|0x00000003  <br/> |Green  <br/> |
|0x00000004  <br/> |Grey  <br/> |
|0x00000005  <br/> |Orange  <br/> |
|0x00000006  <br/> |Cyan  <br/> |
|0x00000007  <br/> |Olive  <br/> |
|0x00000008  <br/> |Purple  <br/> |
|0x00000009  <br/> |Teal  <br/> |
|0x0000000A  <br/> |Yellow  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCAL]](https://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

