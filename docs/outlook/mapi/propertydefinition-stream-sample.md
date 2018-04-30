---
title: "PropertyDefinition Stream Sample"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 7919f4d7-04df-4a96-a5b1-b7b460890486
description: "Last modified: March 09, 2015"
---

# PropertyDefinition Stream Sample

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
This topic describes an example of a PropertyDefinition stream. The stream contains a definition of a user-defined field,  `TextField1`. The type is **Text**, and the definition is in the PropDefV2 format.
  
## Data Dump

The following is a data dump of the stream as it would be displayed in a binary editor.
  
|**Stream offset**|**Data bytes**|**ASCII data**|
|:-----|:-----|:-----|
| `0000000000` <br/> | `03 01 01 00 00 00 45 00 00 00 08 00 00 00 00 00` <br/> | `???...E...?.....` <br/> |
| `0000000010` <br/> | `0A 00 54 00 65 00 78 00 74 00 46 00 69 00 65 00` <br/> | `?.T.e.x.t.F.i.e.` <br/> |
| `0000000020` <br/> | `6C 00 64 00 31 00 0A 54 65 78 74 46 69 65 6C 64` <br/> | `l.d.1.?TextField` <br/> |
| `0000000030` <br/> | `31 00 00 00 00 00 00 00 00 15 00 00 00 0A 54 00` <br/> | `1........?...?T.` <br/> |
| `0000000040` <br/> | `65 00 78 00 74 00 46 00 69 00 65 00 6C 00 64 00` <br/> | `e.x.t.F.i.e.l.d.` <br/> |
| `0000000050` <br/> | `31 00 00 00 00 00` <br/> | `1.....` <br/> |
   
The following is a parse of the sample data for the PropertyDefinition stream:
  
- Version: Offset 0x0, 2 bytes: 0x0103 (PropDefV2).
    
- FieldDefinitionCount: Offset 0x2, 4 bytes: 0x1 (1).
    
- FieldDefinitions: Offset 0x6, array of 1 FieldDefinition stream.
    
  - Flags: Offset 0x6, 4 bytes: 0x45 (PDO_IS_CUSTOM|PDO_PRINT_SAVEAS|PDO_PRINT_SAVEAS_DEF).
    
  - VT: Offset 0xA, 2 bytes: 0x8 ( **VT_BSTR**).
    
  - DispId: Offset 0xC, 4 bytes: 0x0 (0).
    
  - NmidNameLength: Offset 0x10, 2 bytes: 0xA (10).
    
  - NmidName: Offset 0x12, array of 10 WCHARs. Unicode string value: "TextField1".
    
  - NameANSI: Offset 0x26, PackedAnsiString stream.
    
  - Length: Offset 0x26, 1 byte: 0xA (10).
    
  - Characters: Offset 0x27, array of 10 CHARs. ANSI string value: "TextField1".
    
  - FormulaANSI: Offset 0x31, PackedAnsiString stream.
    
  - Length: Offset 0x31, 1 byte: 0x0 (0).
    
  - Characters: Offset 0x32, array of 0 CHARs. Empty ANSI string.
    
  - ValidationRuleANSI: Offset 0x32, PackedAnsiString stream.
    
  - Length: Offset 0x32, 1 byte: 0x0 (0).
    
  - Characters: Offset 0x33, array of 0 CHARs. Empty ANSI string.
    
  - ValidationTextANSI: Offset 0x33, PackedAnsiString stream.
    
  - Length: Offset 0x33, 1 byte: 0x0 (0).
    
  - Characters: Offset 0x34, array of 0 CHARs. Empty ANSI string.
    
  - ErrorANSI: Offset 0x34, PackedAnsiString stream.
    
  - Length: Offset 0x34, 1 byte: 0x0 (0).
    
  - Characters: Offset 0x35, array of 0 CHARs. Empty ANSI string.
    
  - InternalType: Offset 0x35, 4 bytes: 0x0 (iTypeString).
    
  - SkipBlocks: Offset 0x39, series of SkipBlock streams.
    
  - First SkipBlock
    
  - Size: Offset 0x39, 4 bytes: 0x15 (21).
    
  - Content: Offset 0x3D, array of 21 bytes. This is the first SkipBlock stream, so this array contains a FirstSkipBlockContent stream.
    
  - FieldName: Offset 0x3D, PackedUnicodeString stream.
    
  - Length: Offset 0x3D, 1 byte: 0xA (10).
    
  - Characters: Offset 0x3E, array of 10 WCHARs. Unicode string value: "TextField1".
    
  - Second SkipBlock
    
  - Size: Offset 0x52, 4 bytes: 0x0 (0). This is the terminating SkipBlock stream.
    
## See also

#### Concepts

[Outlook Items and Fields](outlook-items-and-fields.md)
  
[Stream Structures](stream-structures.md)
  
[PropertyDefinition Stream Structure](propertydefinition-stream-structure.md)
  
[FieldDefinition Stream Structure](fielddefinition-stream-structure.md)
  
[SkipBlock Stream Structure](skipblock-stream-structure.md)
  
[FirstSkipBlockContent Stream Structure](firstskipblockcontent-stream-structure.md)
  
[PackedAnsiString Stream Structure](packedansistring-stream-structure.md)
  
[PackedUnicodeString Stream Structure](packedunicodestring-stream-structure.md)

