---
title: "PidTagControlId Canonical Property"
description: Outlines the PidTagControlId canonical property, which contains a unique identifier for a control used in a dialog box.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagControlId
api_type:
- HeaderDef
ms.assetid: 281bc3e0-7c69-461b-bf09-4281abbb5e1b
---

# PidTagControlId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a unique identifier for a control used in a dialog box. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTROL_ID  <br/> |
|Identifier:  <br/> |0x3F07  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI display table  <br/> |
   
## Remarks

This property contains a unique identifier for the control. This identifier should contain a [GUID](guid.md) structure and a binary value of type **LONG**. All controls in the dialog box should use the same **GUID** to identify the service provider, and each control should use a unique **LONG** value to ensure that the controls do not collide. 
  
This property is used in notifications. For example, notifications sent on the display table must set this property to uniquely identify the control to update. 
  
## Related resources

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

