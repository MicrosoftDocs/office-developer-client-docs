---
title: "Add a Definition for a New User-Defined Field"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 183d3b86-4506-44da-bbfc-d6242ad89e57
description: "Last modified: July 23, 2011"
 
 
---

# Add a Definition for a New User-Defined Field

  
  
**Applies to**: Outlook 
  
When you add a user-defined field to a Microsoft Outlook item, you add a field definition to the corresponding [PropertyDefinition](propertydefinition-stream-structure.md) stream structure. Use the following procedure to add a new field definition to a PropertyDefinition stream structure. 
  
### To add a definition for a new user-defined field

1. Copy the existing field definitions of the PropertyDefinition stream structure to a new field definitions array. 
    
2. If any existing field definitions are in the PropDefV1 format, convert them to the PropDefV2 format. For more information about field definition formats, see [PropertyDefinition Stream Structure](propertydefinition-stream-structure.md) and [FieldDefinition Stream Structure](fielddefinition-stream-structure.md).
    
3. Create a definition of the new user-defined field in the PropDefV2 format and add it to the array.
    
4. Set the Version element of the PropertyDefinition stream structure as 0x0103, if the Version element has not been set to that value.
    
5. Increment the FieldDefinitionCount element by 1.
    
6. Store the array as the value of the FieldDefinitions element.
    
## See also

#### Concepts

[PropertyDefinition Stream Structure](propertydefinition-stream-structure.md)

