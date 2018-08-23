---
title: "PackedAnsiString Stream Structure"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: ada86f04-e81b-4f97-b9c1-1c8ec5e1a5dd
description: "Last modified: July 23, 2011"
 
 
---

# PackedAnsiString Stream Structure

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The PackedAnsiString stream structure contains an ANSI representation of a string, based on the ANSI code page of the computer on which Microsoft Outlook is running. This string is not terminated by a null character. Data elements in this stream are stored in little-endian byte order, immediately following each other in the order listed below. The actual data elements that exist depend on the length of the string in ANSI representation.
  
- For a string whose ANSI representation contains less than 255 bytes, the data elements are as follows:
    
  - Length: BYTE (1 byte), the length, in number of bytes, of the ANSI representation of the string.
    
  - Characters: An array of CHAR. The count of this array is equal to the Length data element. The data in the array is the ANSI representation of the string.
    
- For a string whose ANSI representation contains 255 to 65535 bytes, the data elements are as follows:
    
  - Prefix: BYTE (1 byte), the value of 255 (0xff).
    
  - Length: WORD (2 bytes), the length, in number of bytes, of the ANSI representation of the string.
    
  - Characters: An array of CHAR. The count of this array is equal to the Length data element. The data in the array is the ANSI representation of the string.
    
## See also



[Outlook Items and Fields](outlook-items-and-fields.md)
  
[Stream Structures](stream-structures.md)
  
[FieldDefinition Stream Structure](fielddefinition-stream-structure.md)

