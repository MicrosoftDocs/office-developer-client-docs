---
title: "PidTagMailPermission Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMailPermission
api_type:
- HeaderDef
ms.assetid: f8270ef2-56d4-4b47-bdda-a39c966bbcba
description: "Contains TRUE if the messaging user is allowed to send and receive messages. Use FALSE in a corporate directory where some of the entries are not email-enabled."
---

# PidTagMailPermission Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains TRUE if the messaging user is allowed to send and receive messages. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_MAIL_PERMISSION  <br/> |
|Identifier:  <br/> |0x3A0E  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Address  <br/> |
   
## Remarks

If this property is not set, MAPI treats it as having a TRUE value. 
  
Set this property to FALSE in a corporate directory where some of the entries are not email-enabled. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

