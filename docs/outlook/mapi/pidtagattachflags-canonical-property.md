---
title: "PidTagAttachFlags Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAttachFlags
api_type:
- HeaderDef
ms.assetid: 47e01131-f399-43cb-9815-aba69638c3fb
description: "Last modified: March 09, 2015"
---

# PidTagAttachFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a bitmask of flags for an attachment. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_FLAGS  <br/> |
|Identifier:  <br/> |0x3714  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

This property is used for MHTML support. 
  
One or more of the following flags can be set for the **PR_ATTACH_FLAGS** bitmask: 
  
ATT_INVISIBLE_IN_HTML 
  
> Indicates that this attachment is not available to HTML rendering applications and should be ignored in Multipurpose Internet Mail Extensions (MIME) processing. 
    
ATT_INVISIBLE_IN_RTF 
  
> Indicates that this attachment is not available to applications rendering in Rich Text Format (RTF) and should be ignored by MAPI.
    
If the **PR_ATTACH_FLAGS** property is zero or absent, the attachment is to be processed by all applications. 
  
## Related resources

### Protocol specifications

[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
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

