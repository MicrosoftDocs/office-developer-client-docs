---
title: Position property (ADO)
TOCTitle: Position property (ADO)
ms:assetid: a07c9197-673b-ddf2-fca9-b0b54fbd67b4
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249738(v=office.15)
ms:contentKeyID: 48546709
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Position property (ADO)


**Applies to**: Access 2013, Office 2013

Indicates the current position within a [Stream](stream-object-ado.md) object.

## Settings and return values

Sets or returns a **Long** value that specifies the offset, in number of bytes, of the current position from the beginning of the stream. The default is 0, which represents the first byte in the stream.

## Remarks

The current position can be moved to a point after the end of the stream. If you specify the current position beyond the end of the stream, the [Size](https://msdn.microsoft.com/library/jj250128\(v=office.15\)) of the **Stream** object will be increased accordingly. Any new bytes added in this way will be null.


> [!NOTE]
> <P><STRONG>Position</STRONG> always measures bytes. For text streams using multibyte character sets, multiply the position by the character size to determine the character number. For example, for a two-byte character set, the first character is at position 0, the second character at position 2, the third character at position 4, and so on.</P>



Negative values cannot be used to change the current position in a **Stream**. Only positive numbers can be used for **Position**.

For read-only **Stream** objects, ADO will not return an error if **Position** is set to a value greater than the **Size** of the **Stream**. This does not change the size of the **Stream**, or alter the **Stream** contents in any way. However, doing this should be avoided because it results in a meaningless **Position** value.

