---
title: "PackedUnicodeString Stream Structure"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: e4cb1613-7e81-432a-ae3a-7fedb05dac65
description: "Last modified: July 23, 2011"
---

# PackedUnicodeString Stream Structure

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
The PackedUnicodeString stream structure contains a Unicode (UTF-16) representation of a string. This string is not terminated by a null character. Data elements in this stream are stored in little-endian byte order, immediately following each other in the order listed below. The actual data elements that exist depend on the length of the string in UTF-16 representation.
  
- For a string whose UTF-16 representation contains less than 255 WCHARs, the data elements are as follows:
    
  - Length: BYTE (1 byte), the length, in number of WCHARs, of the UTF-16 representation of the string.
    
  - Characters: An array of WCHAR. The count of this array is equal to the Length data element. The data in the array is the UTF-16 representation of the string.
    
- For a string whose UTF-16 representation contains 255 to 65535 WCHARs, the data elements are as follows:
    
  - Prefix: BYTE (1 byte), the value of 255 (0xff).
    
  - Length: WORD (2 bytes), the length, in number of WCHARs, of the UTF-16 representation of the string.
    
  - Characters: An array of WCHAR. The count of this array is equal to the Length data element. The data in the array is the UTF-16 representation of the string.
    
## See also

#### Concepts

[Outlook Items and Fields](outlook-items-and-fields.md)
  
[Stream Structures](stream-structures.md)
  
[FieldDefinition Stream Structure](fielddefinition-stream-structure.md)

