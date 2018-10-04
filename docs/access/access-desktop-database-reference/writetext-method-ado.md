﻿---
title: WriteText Method (ADO)
TOCTitle: WriteText Method (ADO)
ms:assetid: 1ca2d9d5-11f4-d088-6fc3-53240208bb09
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248963(v=office.15)
ms:contentKeyID: 48543574
ms.date: 09/18/2015
mtps_version: v=office.15
---

# WriteText Method (ADO)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameters  
Remarks  

Writes a specified text string to a [Stream](stream-object-ado.md) object.

## Syntax

*Stream*.WriteText*Data*, *Options*

## Parameters

  - *Data*

  - A **String** value that contains the text in characters to be written.

  - *Options*

  - Optional. A [StreamWriteEnum](streamwriteenum.md) value that specifies whether a line separator character must be written at the end of the specified string.

## Remarks

Specified strings are written to the **Stream** object without any intervening spaces or characters between each string.

The current [Position](position-property-ado.md) is set to the character following the written data. The **WriteText** method does not truncate the rest of the data in a stream. If you want to truncate these characters, call [SetEOS](seteos-method-ado.md).

If you write past the current [EOS](eos-property-ado.md) position, the [Size](https://msdn.microsoft.com/library/jj250128\(v=office.15\)) of the **Stream** will be increased to contain any new characters, and **EOS** will move to the new last byte in the **Stream**.


> [!NOTE]
> <P>The <STRONG>WriteText</STRONG> method is used with text streams (<A href="type-property-ado-stream.md">Type</A> is <STRONG>adTypeText</STRONG>). For binary streams (<STRONG>Type</STRONG> is <STRONG>adTypeBinary</STRONG>), use <A href="write-method-ado.md">Write</A>.</P>


