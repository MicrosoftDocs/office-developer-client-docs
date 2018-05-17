---
title: "PidTagMailPermission Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagMailPermission
api_type:
- HeaderDef
ms.assetid: f8270ef2-56d4-4b47-bdda-a39c966bbcba
description: "Last modified: March 09, 2015"
---

# PidTagMailPermission Canonical Property

  
  
**Applies to**: Outlook 
  
Contains TRUE if the messaging user is allowed to send and receive messages. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MAIL_PERMISSION  <br/> |
|Identifier:  <br/> |0x3A0E  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Address  <br/> |
   
## Remarks

If this property is not set, MAPI treats it as having a TRUE value. 
  
Set this property to FALSE in a corporate directory where some of the entries are not e-mail-enabled. 
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

