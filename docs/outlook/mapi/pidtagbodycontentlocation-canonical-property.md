---
title: "PidTagBodyContentLocation Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagBodyContentLocation
api_type:
- HeaderDef
ms.assetid: a66d1c64-5c5a-4980-9acd-72448108fd2c
description: "Last modified: March 09, 2015"
---

# PidTagBodyContentLocation Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the value of a MIME Content-Location header field.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_BODY_CONTENT_LOCATION, PR_BODY_CONTENT_LOCATION_A, PR_BODY_CONTENT_LOCATION_W  <br/> |
|Identifier:  <br/> |0x1014  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MIME  <br/> |
   
## Remarks

To set the value of these properties, MIME clients should write the desired value to a Content-Location header field on a MIME entity that maps to a message body.
  
MIME readers should copy the value of a Content-Location header field on such a MIME entity to the value of these properties.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMAIL]](https://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard email conventions to message objects.
    
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

