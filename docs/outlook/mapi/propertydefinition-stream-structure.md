---
title: "PropertyDefinition stream structure"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: ab677a06-6d7d-47e7-99ea-535b0b24389a
description: "Last modified: March 09, 2015"
 
 
---

# PropertyDefinition stream structure

**Applies to**: Outlook 2013 | Outlook 2016 
  
A PropertyDefinition stream structure is an array of [FieldDefinition](fielddefinition-stream-structure.md) stream structures that contain definitions for all user-defined fields in a Microsoft Outlook item, and data-binding settings for some built-in fields. 
  
You can programmatically manipulate the PropertyDefinition stream structure. However, you can achieve similar results by using the Outlook Forms Designer and, in particular, the **Properties** dialog box for a data-bound control. 
  
Field definitions in a PropertyDefinition stream structure can be one of two formats: PropDefV1 and PropDefV2. Outlook supports both PropDefV1 and PropDefV2. All field definitions in a single PropertyDefinition stream structure must be of the same format. For more information about how PropDefV1 and PropDefV2 differ, see [FieldDefinition Stream Structure](fielddefinition-stream-structure.md).
  
Data elements in this stream are stored in little-endian byte order, immediately following each other in the order specified below.
  
- Version: WORD (2 bytes), the format of the field definitions in the PropertyDefinition stream structure. The following table shows the possible values.
    
    |**Value**|**Description**|
    |:-----|:-----|
    |0x0102  <br/> |Format is PropDefV1.  <br/> |
    |0x0103  <br/> |Format is PropDefV2.  <br/> |
   
- FieldDefinitionCount: DWORD (4 bytes), the number of field definitions in this stream. This is the count of array elements in the FieldDefinitions data element.
    
- FieldDefinitions: An array of FieldDefinition stream structures. The count of this array is equal to the FieldDefinitionCount data element.
    
## See also

- [Outlook Items and Fields](outlook-items-and-fields.md)
- [Add a Definition for a New User-Defined Field](how-to-add-a-definition-for-a-new-user-defined-field.md)
- [PropertyDefinition Stream Sample](propertydefinition-stream-sample.md)
- [Stream Structures](stream-structures.md)

