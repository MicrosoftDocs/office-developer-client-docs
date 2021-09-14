---
title: "SkipBlock Stream Structure"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 2499587b-2a0e-4987-9bf7-591bef41b894
description: "Last modified: July 23, 2011"
 
 
---

# SkipBlock Stream Structure

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A SkipBlock stream structure is a block of data that starts with an integer that specifies the length of the remaining part of the block. This stream structure exists in a [FieldDefinition](fielddefinition-stream-structure.md) stream if the field definition is in PropDefV2 format. 
  
The purpose of a SkipBlock stream structure depends on its relative location in a series of like structures in the SkipBlocks data element of a FieldDefinition stream. The SkipBlocks series should contain at least one SkipBlock structure that terminates the series and has the Size data element equal to 0. If the first structure is not the terminating structure (that is, the Size data element is greater than 0), Outlook assumes the first structure specifies the field name in Unicode (UTF-16).
  
Data elements in this stream are stored in little-endian byte order, immediately following each other in the order specified below.
  
- Size: DWORD (4 bytes), the size, in number of bytes, of the Content data element.
    
- Content: An array of BYTE. The count of this array is equal to the Size data element. The meaning of the Content data element depends on the location of the SkipBlock structure in the series and the version of Outlook. If the first SkipBlock structure is not the terminating structure, Outlook considers the first SkipBlock structure as the [FirstSkipBlockContent](firstskipblockcontent-stream-structure.md) stream structure that specifies the field name in Unicode. 
    
## See also



[Outlook Items and Fields](outlook-items-and-fields.md)
  
[Stream Structures](stream-structures.md)
  
[FieldDefinition Stream Structure](fielddefinition-stream-structure.md)
  
[FirstSkipBlockContent Stream Structure](firstskipblockcontent-stream-structure.md)

