---
title: "PidLidSmartNoAttach Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidSmartNoAttach
api_type:
- COM
ms.assetid: 60299c1b-1b46-4c3a-8fb9-a2b4d3383aac
description: "Last modified: March 09, 2015"
---

# PidLidSmartNoAttach Canonical Property

  
  
**Applies to**: Outlook 
  
Represents whether the attachments on a message are considered as hidden.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidSmartNoAttach  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008514  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Run-time configuration  <br/> |
   
## Remarks

This property is TRUE if the attachments of the message are considered as hidden.
  
It indicates whether the message object has no end-user visible attachments. This property may be unset; if so, a default value of FALSE is assumed.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definition and references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

