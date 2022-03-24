---
title: "PidLidNonSendCcTrackStatus Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidNonSendCcTrackStatus
api_type:
- COM
ms.assetid: e2654fad-444b-45bc-976d-3c5cbbc81b84
description: "Last modified: March 09, 2015"
---

# PidLidNonSendCcTrackStatus Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the value for each attendee listed in the **dispidNonSendableCC** ([PidLidNonSendableCc](pidlidnonsendablecc-canonical-property.md)) property.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |dispidNonSendCcTrackStatus  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008544  <br/> |
|Data type:  <br/> |PT_MV_LONG  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

This property is required only when the **dispidNonSendableCC** property is set. The number of values in this property must equal the number of values in **dispidNonSendableCC**. Each PT_LONG value in this property corresponds to the attendee in the **dispidNonSendableCC** property at the same index. 
  
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

