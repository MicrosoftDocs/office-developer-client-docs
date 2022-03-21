---
title: "PidLidPropertyDefinitionStream Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidPropertyDefinitionStream
api_type:
- COM
ms.assetid: ead35049-e60e-4b46-bf12-f73d77cd36b2
description: "Last modified: March 09, 2015"
---

# PidLidPropertyDefinitionStream Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Represents definitions of user-defined fields and data-binding settings of built-in fields of a message.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidPropDefStream  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008540  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Run-time configuration  <br/> |
   
## Remarks

The value of the **PidLidPropertyDefinitionStream** property is saved as part of the custom form definition for the message. 
  
The value of this property is a binary stream. For information on the structure of this stream, see [PropertyDefinition Stream Structure](propertydefinition-stream-structure.md). 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[Outlook Items and Fields](outlook-items-and-fields.md)
  
[Add a Definition for a New User-Defined Field](how-to-add-a-definition-for-a-new-user-defined-field.md)
  
[PropertyDefinition Stream Sample](propertydefinition-stream-sample.md)
  
[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

