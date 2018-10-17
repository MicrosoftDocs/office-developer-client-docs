---
title: ReadText Method (ADO)
TOCTitle: ReadText Method (ADO)
ms:assetid: 08f5bac4-dccd-696c-09a7-e1ba0cb38d79
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248826(v=office.15)
ms:contentKeyID: 48543108
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ReadText Method (ADO)


**Applies to**: Access 2013 | Office 2013

Reads specified number of characters from a text [Stream](stream-object-ado.md) object.

## Syntax

*String* = *Stream*.ReadText (*NumChars*)

## Parameters

  - *NumChars*

  - Optional. A **Long** value that specifies the number of characters to read from the file, or a [StreamReadEnum](streamreadenum.md) value. The default value is **adReadAll**.

<<<<<<< HEAD
## Return Value
=======
## Return value
>>>>>>> master

The **ReadText** method reads a specified number of characters, an entire line, or the entire stream from a **Stream** object and returns the resulting string.

## Remarks

If *NumChar* is more than the number of characters left in the stream, only the characters remaining are returned. The string read is not padded to match the length specified by *NumChar*. If there are no characters left to read, a variant whose value is null is returned. **ReadText** cannot be used to read backwards.


> [!NOTE]
> <P>The <STRONG>ReadText</STRONG> method is used with text streams (<A href="type-property-ado-stream.md">Type</A> is <STRONG>adTypeText</STRONG>). For binary streams (<STRONG>Type</STRONG> is <STRONG>adTypeBinary</STRONG>), use <A href="read-method-ado.md">Read</A>.</P>


