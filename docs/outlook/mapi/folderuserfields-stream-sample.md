---
title: "FolderUserFields stream sample"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 30e5e887-a324-4ed2-ba2a-eb4c19ba38d2
description: "Last modified: March 09, 2015"
---

# FolderUserFields stream sample

**Applies to**: Outlook 
  
This topic describes an example of a FolderUserFields stream. The stream contains a definition of a user-defined field,  `TextField1`. The type is **Text**, and the FolderUserFields stream contains both FolderUserFieldsAnsi and FolderUserFieldsUnicode parts. For more information see [Folder Fields Stream Structures](folder-fields-stream-structures.md).
  
## Data dump

The following is a data dump of the stream as it would be displayed in a binary editor.
  
|Stream offset|Data bytes|ASCII data|
|:-----|:-----|:-----|
| `0000000000` <br/> | `02 00 00 00 01 00 00 00 0A 00 54 65 78 74 46 69` <br/> | `..........TextFi` <br/> |
| `0000000010` <br/> | `65 6C 64 31 29 03 02 00 00 00 00 00 C0 00 00 00` <br/> | `eld1).......A...` <br/> |
| `0000000020` <br/> | `00 00 00 46 07 00 00 80 00 00 00 00 00 00 00 00` <br/> | `...F............` <br/> |
| `0000000030` <br/> | `00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00` <br/> | `................` <br/> |
| `0000000040` <br/> | `00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00` <br/> | `................` <br/> |
| `0000000050` <br/> | `00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00` <br/> | `................` <br/> |
| `0000000060` <br/> | `00 00 00 00 00 00 02 00 00 00 01 00 00 00 0A 00` <br/> | `................` <br/> |
| `0000000070` <br/> | `54 00 65 00 78 00 74 00 46 00 69 00 65 00 6C 00` <br/> | `T.e.x.t.F.i.e.l.` <br/> |
| `0000000080` <br/> | `64 00 31 00 29 03 02 00 00 00 00 00 C0 00 00 00` <br/> | `d.1.).......A...` <br/> |
| `0000000090` <br/> | `00 00 00 46 07 00 00 80 00 00 00 00 00 00 00 00` <br/> | `...F............` <br/> |
| `00000000A0` <br/> | `00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00` <br/> | `................` <br/> |
| `00000000B0` <br/> | `00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00` <br/> | `................` <br/> |
| `00000000C0` <br/> | `00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00` <br/> | `................` <br/> |
| `00000000D0` <br/> | `00 00 00 00 00 00` <br/> | `......` <br/> |
   

The following is a parse of the sample data for the **FolderUserFields** stream:
  
- FolderUserFieldsAnsi: Offset 0x0.
    
  - FieldDefinitionCount: Offset 0x0, 4 bytes: 0x00000002 (2).
    
  - FieldDefinitions: Offset 0x4, array of 2 FolderFieldDefinitionA streams.
    
    **First array element**:
    
    - FieldType: Offset 0x4, 4 bytes: 0x00000001 (ftString).
      
    - FieldNameLength: Offset 0x8, 2 bytes: 0x000A (10)
      
    - FieldName: Offset 0xA, array of 10 CHARs. ANSI string value: "TextField1".
      
    - Common: Offset 0x14.
    
      - PropSetGuid: Offset 0x14, 16 bytes: {00020329-0000-0000-C000-000000000046} (PS_PUBLIC_STRINGS).
        
      - fcapm: Offset 0x24, 4 bytes: 0x80000007 (FCAPM_CAN_EDIT| FCAPM_CAN_SORT| FCAPM_CAN_GROUP|FCAPM_CAN_EDIT_IN_ITEM).
        
      - dwString: Offset 0x28, 4 bytes: 0x00000000.
        
      - dwBitmap: Offset 0x2C, 4 bytes: 0x00000000.
        
      - dwDisplay: Offset 0x30, 4 bytes: 0x00000000.
        
      - iFmt: Offset 0x34, 4 bytes: 0x00000000.
        
      - wszFormulaLength: Offset 0x38, 2 bytes: 0x0000 (0).
        
      - wszFormula: Offset 0x3A, array of 0 WCHARs. Empty string value.
    
    **Second array element**:
    
    - FieldType: Offset 0x3A, 4 bytes: 0x00000000 (ftNone).
      
    - FieldNameLength: Offset 0x3E, 2 bytes: 0x0000 (0).
      
    - FieldName: Offset 0x40, array of 0 CHARs. Empty string value.
      
    - Common: Offset 0x40.
    
      - PropSetGuid: Offset 0x40, 16 bytes: {00000000-0000-0000-0000-000000000000} (GUID_NULL).
        
      - fcapm: Offset 0x50, 4 bytes: 0x00000000 (0).
        
      - dwString: Offset 0x54, 4 bytes: 0x00000000.
        
      - dwBitmap: Offset 0x58, 4 bytes: 0x00000000.
        
      - dwDisplay: Offset 0x5C, 4 bytes: 0x00000000.
        
      - iFmt: Offset 0x60, 4 bytes: 0x00000000.
        
      - wszFormulaLength: Offset 0x64, 2 bytes: 0x0000 (0).
        
      - wszFormula: Offset 0x66, array of 0 WCHARs. Empty string value.
    
- FolderUserFieldsUnicode: Offset 0x66.
    
  - FieldDefinitionCount: Offset 0x66, 4 bytes: 0x00000002 (2).
    
  - FieldDefinitions: Offset 0x6A, array of 2 FolderFieldDefinitionW streams.
    
    **First array element**:
    
    - FieldType: Offset 0x6A, 4 bytes: 0x00000001 (ftString).
      
    - FieldNameLength: Offset 0x6E, 2 bytes: 0x000A (10).
      
    - FieldName: Offset 0x70, array of 10 WCHARs. Unicode string value: "TextField1".
      
    - Common: Offset 0x84.
    
      - PropSetGuid: Offset 0x84, 16 bytes: {00020329-0000-0000-C000-000000000046} (PS_PUBLIC_STRINGS).
        
      - fcapm: Offset 0x94, 4 bytes: 0x80000007 (FCAPM_CAN_EDIT| FCAPM_CAN_SORT| FCAPM_CAN_GROUP|FCAPM_CAN_EDIT_IN_ITEM).
        
      - dwString: Offset 0x98, 4 bytes: 0x00000000.
        
      - dwBitmap: Offset 0x9C, 4 bytes: 0x00000000.
        
      - dwDisplay: Offset 0xA0, 4 bytes: 0x00000000.
        
      - iFmt: Offset 0xA4, 4 bytes: 0x00000000.
        
      - wszFormulaLength: Offset 0xA8, 2 bytes: 0x0000 (0).
        
      - wszFormula: Offset 0xAA, array of 0 WCHARs. Empty string value.
    
    **Second array element**:
    
    - FieldType: Offset 0xAA, 4 bytes: 0x00000000 (ftNone).
      
    - FieldNameLength: Offset 0xAE, 2 bytes: 0x0000 (0).
      
    - FieldName: Offset 0xB0, array of 0 WCHARs. Empty string value.
      
    - Common: Offset 0xB0.
    
      - PropSetGuid: Offset 0xB0, 16 bytes: {00000000-0000-0000-0000-000000000000} (GUID_NULL).
        
      - fcapm: Offset 0xC0, 4 bytes: 0x00000000 (0).
        
      - dwString: Offset 0xC4, 4 bytes: 0x00000000.
        
      - dwBitmap: Offset 0xC8, 4 bytes: 0x00000000.
        
      - dwDisplay: Offset 0xCC, 4 bytes: 0x00000000.
        
      - iFmt: Offset 0xD0, 4 bytes: 0x00000000.
        
      - wszFormulaLength: Offset 0xD4, 2 bytes: 0x0000 (0).
        
      - wszFormula: Offset 0xD6, array of 0 WCHARs. Empty string value.
    
## See also

- [Outlook Items and Fields](outlook-items-and-fields.md)
- [PropertyDefinition Stream Structure](propertydefinition-stream-structure.md)
- [FieldDefinition Stream Structure](fielddefinition-stream-structure.md)
- [SkipBlock Stream Structure](skipblock-stream-structure.md)
- [FirstSkipBlockContent Stream Structure](firstskipblockcontent-stream-structure.md)
- [PackedAnsiString Stream Structure](packedansistring-stream-structure.md)
- [PackedUnicodeString Stream Structure](packedunicodestring-stream-structure.md)

