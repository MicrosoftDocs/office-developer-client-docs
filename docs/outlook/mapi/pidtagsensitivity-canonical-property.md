---
title: "PidTagSensitivity Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagSensitivity
api_type:
- COM
ms.assetid: 5b678475-f2a8-4831-ad68-11654e09c821
description: "Last modified: March 09, 2015"
---

# PidTagSensitivity Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a value that indicates the message sender's opinion of the sensitivity of a message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SENSITIVITY  <br/> |
|Identifier:  <br/> |0x0036  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

It is recommended that message objects expose this property.
  
This property can have exactly one of the following values:
  
SENSITIVITY_NONE 
  
> The message has no special sensitivity.
    
SENSITIVITY_PERSONAL 
  
> The message is personal.
    
SENSITIVITY_PRIVATE 
  
> The message is private.
    
SENSITIVITY_COMPANY_CONFIDENTIAL 
  
> The message is designated company confidential.
    
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
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

