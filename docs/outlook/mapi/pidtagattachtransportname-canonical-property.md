---
title: "PidTagAttachTransportName Canonical Property"
description: Outlines the PidTagAttachTransportName canonical property, which contains the name of an attachment file modified so it can be associated with TNEF messages. 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagAttachTransportName
api_type:
- HeaderDef
ms.assetid: 701fca52-0f96-4019-80cd-c0ccd059ff9b
---

# PidTagAttachTransportName Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the name of an attachment file modified so that it can be associated with TNEF messages. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_TRANSPORT_NAME, PR_ATTACH_TRANSPORT_NAME_A, PR_ATTACH_TRANSPORT_NAME_W  <br/> |
|Identifier:  <br/> |0x370C  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

TNEF and the transport provider use these properties. They are usually not available to client applications. 
  
These properties are commonly used by TNEF when the underlying messaging system does not support the supplied filenames. For example, they are used when the user attaches multiple files with the same name, such as five files named CONFIG.SYS. The transport provider must modify the names to make sure they are unique. Each modified name appears in its attachment's **PR_ATTACH_TRANSPORT_NAME** and associated properties. 
  
## Related resources

### Protocol specifications

[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
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

