---
title: "PidTagAttachContentLocation Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAttachContentLocation
api_type:
- HeaderDef
ms.assetid: af2f776c-1b77-4942-827a-4363eda3924f
description: "Last modified: March 09, 2015"
---

# PidTagAttachContentLocation Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the content location header of a Multipurpose Internet Mail Extensions (MIME) message attachment. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_CONTENT_LOCATION, PR_ATTACH_CONTENT_LOCATION_A, PR_ATTACH_CONTENT_LOCATION_W  <br/> |
|Identifier:  <br/> |0x3713  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

These properties are used for MHTML support. They represent the content location header for the appropriate MIME body part. 
  
## Related Resources

### Protocol Specifications

[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

