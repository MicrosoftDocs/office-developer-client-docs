---
title: "PidTagExtendedFolderFlags Canonical Property"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagExtendedFolderFlags
api_type:
- HeaderDef
ms.assetid: e0c04f98-3d66-4ab5-ba05-69f9df539fcf
description: "Last modified: March 09, 2015"
---

# PidTagExtendedFolderFlags Canonical Property
 
**Applies to**: Outlook 
  
Contains extended flags about a folder.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_EXTENDED_FOLDER_FLAGS  <br/> |
|Identifier:  <br/> |0x36DA  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI container  <br/> |
   
## Remarks

This property is a binary stream that contains encoded sub-properties for the folder. It is formatted as a series of variable length sub items. The first 8 bits of the sub item is an ID field, which indicates what kind of flag the sub item represents. The second 8 bits is the number of bytes of data that follow.
  
Possible ID values include:
  
- Invalid
    
   Do not use this value
    
- ExtendedFlags
    
   The data is a four byte value formatted as:
    
|**Bits**|**Description**|
|:-----|:-----|
|0-1  <br/> |Reserved.  <br/> |
|2  <br/> |Set to 0 if the application should show a policy description.  <br/> |
|3-5  <br/> |Reserved.  <br/> |
|6-7  <br/> |Controls the display of the number of messages in the folder.  <br/> 0 - Use the default setting  <br/> 1 - Use the number of unread messages  <br/> 3 - Use the total number of messages  <br/> |
|8-31  <br/> |Reserved.  <br/> |
   
Reserved items can be ignored, but existing values must be preserved.
    
- SearchFolderID
    
   The data field is a 16-byte field. When the application creates a persistent search folder, it must set this field on the folder to the same value as the **PR_WB_SF_TAG** ([PidTagSearchFolderId)](pidtagsearchfolderid-canonical-property.md)) binary property on the Search Folder Message.
    
- ToDoFolderVersion
    
   The data field is a 4-byte field. When the application creates the to-do search folder, it must set the value of this field on the folder to the little-endian integer value of" 0x000c0000":
    
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOCFG]](http://msdn.microsoft.com/library/7d466dd5-c156-4da9-9a01-75c78e7e1a67%28Office.15%29.aspx)
  
> Specifies the location and properties of client and server configuration data, such as shared category lists and working hours.
    
[[MS-OXOSRCH]](http://msdn.microsoft.com/library/c72e49b8-78c7-4483-ad65-e46e9133673b%28Office.15%29.aspx)
  
> Specifies the properties and operations for manipulating a search folder list configuration.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

