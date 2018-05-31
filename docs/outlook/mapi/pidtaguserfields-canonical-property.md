---
title: "PidTagUserFields Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: db3a6947-f640-43e8-a2df-71e96560fd81
description: "Last modified: March 09, 2015"
---

# PidTagUserFields Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the name, data type, and other information about a user-defined field.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_USERFIELDS  <br/> |
|Identifier:  <br/> |0x36E3  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI folder  <br/> |
   
## Remarks

For each item, Outlook stores the definitions of all user-defined fields in the [PidLidPropertyDefinitionStream](pidlidpropertydefinitionstream-canonical-property.md) property of the corresponding **IMessage** object. The **PidLidPropertyDefinitionStream** property contains a binary stream known as [PropertyDefinition](propertydefinition-stream-structure.md), which contains the field definitions. For more information about stream structures for field definitions, see [Stream Structures](stream-structures.md).
  
For each folder, Outlook stores the definitions of all user-defined fields in that folder in the **PidTagUserFields** property of an associated message of the message class IPC.MS.REN.USERFIELDS - each folder presumed to contain no more than one message of this class in its associated contents table. 
  
> [!NOTE]
> The set of user-defined fields in a folder may not necessarily match the sets of user-defined fields in each of its items. 
  
The set of user-defined fields in a folder is displayed in various places in the Outlook UI, such as the folder's Field Chooser. The message's **PidTagUserFields** property contains a binary stream, **FolderUserFields**, which contains the folder field definitions. For more information about stream structures for folder field definitions, see [Folder Fields Stream Structures](folder-fields-stream-structures.md) and the [FolderUserFields Stream Sample](folderuserfields-stream-sample.md).
  
## Section Heading

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
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

