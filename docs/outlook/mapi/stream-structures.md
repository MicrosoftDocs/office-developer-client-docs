---
title: "Stream Structures"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 9e305071-b6a5-4bd8-892e-25553d04bb15
description: "Last modified: July 23, 2011"
 
 
---

# Stream Structures

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Definitions of user-defined fields of a Microsoft Outlook item are stored in the [PidLidPropertyDefinitionStream](pidlidpropertydefinitionstream-canonical-property.md) property. The value of this property is a binary stream that contains definitions of user-defined fields and data-binding settings for built-in fields for the Outlook item. This section provides information about the structure of the binary stream, broken down in the following stream structures. 
  
> [!NOTE]
> The names of these stream structures (for example, PropertyDefinition, FieldDefinition, and SkipBlock) and their data elements are not technically part of the programming interface of the Messaging API (MAPI), and are provided here only for documentation purposes of the actual stream structures. Developers can label these stream structures and data elements in their applications as they choose. 
  
- [PropertyDefinition Stream Structure](propertydefinition-stream-structure.md)
    
- [FieldDefinition Stream Structure](fielddefinition-stream-structure.md)
    
- [SkipBlock Stream Structure](skipblock-stream-structure.md)
    
- [FirstSkipBlockContent Stream Structure](firstskipblockcontent-stream-structure.md)
    
- [PackedAnsiString Stream Structure](packedansistring-stream-structure.md)
    
- [PackedUnicodeString Stream Structure](packedunicodestring-stream-structure.md)
    
## See also



[Outlook Items and Fields](outlook-items-and-fields.md)
  
[Add a Definition for a New User-Defined Field](how-to-add-a-definition-for-a-new-user-defined-field.md)
  
[PropertyDefinition Stream Sample](propertydefinition-stream-sample.md)

