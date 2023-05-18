---
title: "PidTagRenderingPosition Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagRenderingPosition
api_type:
- COM
ms.assetid: bce46687-17dc-4a3f-96be-303d8755158e
description: "Contains an offset, in characters, to use in rendering an attachment within the main message text. This property should not be used with Rich Text Format (RTF) text."
---

# PidTagRenderingPosition Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an offset, in characters, to use in rendering an attachment within the main message text.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_RENDERING_POSITION  <br/> |
|Identifier:  <br/> |0x370B  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI attachment  <br/> |
   
## Remarks

When the supplied offset is -1 (0xFFFFFFFF), the attachment is not rendered by using this property. All values other than -1 indicate the position within the **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) property at which the attachment is to be rendered.
  
 **Note** The character indicated by this property in **PR_BODY** is replaced by the attachment. Typically this character is a space, although a special placeholder character can also be used. 
  
This property is expressed in characters. In some character sets this is not equivalent to bytes. Unicode applications can compute the position based on two-byte characters. Double-Byte Character Set (DBCS) applications must scan the text up to this property value, because their character representation varies between one and two bytes per character.
  
This property should not be used with Rich Text Format (RTF) text. The rendering position is indicated in RTF by an escape sequence called the object attachment placeholder. This sequence consists of the string  `\objattph` followed by a single character, normally a space, that will be replaced by the attachment rendering. 
  
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

