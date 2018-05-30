---
title: "PidTagRoamingBinary Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f06bf063-fc95-46f9-b5fa-3f127a59ebda
description: "Last modified: March 09, 2015"
---

# PidTagRoamingBinary Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a message stream associated with a subclass of the **IPM.Configuration** class. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ROAMING_BINARYSTREAM  <br/> |
|Identifier:  <br/> |0x7C09  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Configuration  <br/> |
   
## Remarks

This property contains the data stream associated with an **IPM.Configuration** message class message. The format of the stream depends on the message class. For instance, a message of class type **IPM.Configuration.Autocomplete** would be formatted as an [Autocomplete Stream](autocomplete-stream.md).
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Microsoft Exchange Server protocol specifications.
    
[[MS-OXOCFG]](http://msdn.microsoft.com/library/7d466dd5-c156-4da9-9a01-75c78e7e1a67%28Office.15%29.aspx)
  
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

