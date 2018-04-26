---
title: "Position Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: a07c9197-673b-ddf2-fca9-b0b54fbd67b4

---

# Position Property (ADO)

Indicates the current position within a [Stream](stream-object-ado.md) object. 
  
## Settings and Return Values

Sets or returns a **Long** value that specifies the offset, in number of bytes, of the current position from the beginning of the stream. The default is 0, which represents the first byte in the stream. 
  
## Remarks

The current position can be moved to a point after the end of the stream. If you specify the current position beyond the end of the stream, the [Size](http://msdn.microsoft.com/library/deb84313-36d1-fa49-e4cd-daecab96f343%28Office.15%29.aspx) of the **Stream** object will be increased accordingly. Any new bytes added in this way will be null. 
  
> [!NOTE]
> **Position** always measures bytes. For text streams using multibyte character sets, multiply the position by the character size to determine the character number. For example, for a two-byte character set, the first character is at position 0, the second character at position 2, the third character at position 4, and so on. 
  
Negative values cannot be used to change the current position in a **Stream**. Only positive numbers can be used for **Position**. 
  
For read-only **Stream** objects, ADO will not return an error if **Position** is set to a value greater than the **Size** of the **Stream**. This does not change the size of the **Stream**, or alter the **Stream** contents in any way. However, doing this should be avoided because it results in a meaningless **Position** value. 
  

