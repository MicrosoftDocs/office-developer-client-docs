---
title: "PidTagDefaultPostMessageClass Canonical Property"
description: Outlines the PidTagDefaultPostMessageClass canonical property, which contains the name of a custom form Message class.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDefaultPostMessageClass
api_type:
- HeaderDef
ms.assetid: 231c288f-547b-4463-9442-1499661b925e
---

# PidTagDefaultPostMessageClass Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the name of a custom form Message class.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_DEF_POST_MSGCLASS  <br/> |
|Identifier:  <br/> |0x36E5  <br/> |
|Data type:  <br/> |PT_STRING8  <br/> |
|Area:  <br/> |MAPI container  <br/> |
   
## Remarks

If this property is set on a folder, the value must contain either exactly the base message class (for example, "IPM.Contact" for a contacts folder or "IPM.Appointment" for a calendar folder), or begin with the base message class (for example, "IPM.Contact.MyContact").
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOCAL]](https://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
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

