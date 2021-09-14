---
title: "Outlook Items and Fields"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 605fab0f-c045-4d2b-a2da-447a111f66a9
description: "Last modified: July 23, 2011"
 
 
---

# Outlook Items and Fields

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Microsoft Outlook provides item types that are specialized for their functionality (for example, mail items, appointments, contacts, tasks, and notes). Outlook provides standard fields for each type of item, commonly referred to as built-in fields. Outlook also allows users to create custom fields, commonly referred to as user-defined fields. Each field is associated with a data type and a value. Examples of data types are **Currency**, **Date/Time**, **Duration**, **Integer**, **Keywords**, and **Text**. Users can define custom fields by using the Forms Designer in Outlook.
  
At the programmability level, each item is represented by an [IMessage](imessageimapiprop.md) object. Each user-defined field is associated with a field definition and a value. 
  
### Field Definition

A field definition includes the name, data type, and other information about the field. For each item, Outlook stores the definitions of all user-defined fields in the [PidLidPropertyDefinitionStream](pidlidpropertydefinitionstream-canonical-property.md) property of the corresponding **IMessage** object. The **PidLidPropertyDefinitionStream** property contains a binary stream known as [PropertyDefinition](propertydefinition-stream-structure.md) that contains the field definitions. For more information about stream structures for field definitions, see [Stream Structures](stream-structures.md).
  
### Field Value

Each user-defined field of an item has a value that is stored in a corresponding named property. That named property is in the PS_PUBLIC_STRINGS property set, and has a Unicode character string as the property name. The data type of the property corresponds to the type of the field. If the property is not present in the **IMessage** object, Outlook assumes a reasonable default value for the property. For example, for a string type, Outlook assumes an empty string if the property is not present. 
  
## See also



[Add a Definition for a New User-Defined Field](how-to-add-a-definition-for-a-new-user-defined-field.md)
  
[PropertyDefinition Stream Sample](propertydefinition-stream-sample.md)
  
[Stream Structures](stream-structures.md)
  
[PropertyDefinition Stream Structure](propertydefinition-stream-structure.md)
  
[FieldDefinition Stream Structure](fielddefinition-stream-structure.md)
  
[SkipBlock Stream Structure](skipblock-stream-structure.md)
  
[FirstSkipBlockContent Stream Structure](firstskipblockcontent-stream-structure.md)
  
[PackedAnsiString Stream Structure](packedansistring-stream-structure.md)
  
[PackedUnicodeString Stream Structure](packedunicodestring-stream-structure.md)

