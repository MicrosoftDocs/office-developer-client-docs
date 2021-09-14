---
title: "PidTagReturnedMessageid Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 1f0f13e2-7554-41fc-a7a9-a90c34181c96
description: "Last modified: March 09, 2015"
---

# PidTagReturnedMessageid Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains TRUE if the original message is being returned with a nonread report.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RETURNED_IPM  <br/> |
|Identifier:  <br/> |0x0033  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

An X.400 transport provider sets this property in the unread report.
  
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

