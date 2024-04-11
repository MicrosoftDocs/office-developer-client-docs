---
title: "PidTagRoamingXmlStream Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagRoamingXmlStream
api_type:
- COM
ms.assetid: ce55b50e-3dbf-4690-9102-c08f35ada82e
description: "Contains an arbitrary XML stream. Other properties in the message might imply specific schemas to use in this property."
---

# PidTagRoamingXmlStream Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an arbitrary XML stream.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ROAMING_XMLSTREAM  <br/> |
|Identifier:  <br/> |0x7C08  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Configuration  <br/> |
   
## Remarks

This property contains an arbitrary stream of XML data. Other properties in the message may imply specific schemas to use in this property.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOCFG]](https://msdn.microsoft.com/library/7d466dd5-c156-4da9-9a01-75c78e7e1a67%28Office.15%29.aspx)
  
> Specifies the location and properties of client and server configuration data, such as shared category lists and working hours.
    
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

