---
title: "PidLidAutoFillLocation Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidAutoFillLocation
api_type:
- COM
ms.assetid: e4db6cae-4730-45d0-8b8a-9bd484c8bd3f
description: "Indicates that the value of the dispidLocation property is set to the PR_DISPLAY_NAME property from the RecipientRow that represents a resource."
---

# PidLidAutoFillLocation Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates that the value of the **dispidLocation** ([PidLidLocation](pidlidlocation-canonical-property.md)) property is set to the **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property from the RecipientRow that represents a resource.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidAutoFillLocation  <br/> |
|Property set:  <br/> |PSETID_Appointment  <br/> |
|Long ID (LID):  <br/> |0x0000823A  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Meetings  <br/> |
   
## Remarks

For more details on RecipientRow, see the Message and Attachment Object protocol as specified in [[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx).
  
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

