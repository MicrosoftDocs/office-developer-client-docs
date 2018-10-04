---
title: LineSeparator Property (ADO)
TOCTitle: LineSeparator Property (ADO)
ms:assetid: 9f1323cd-d4ed-2bfa-554b-faebab529548
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249729(v=office.15)
ms:contentKeyID: 48546676
ms.date: 09/18/2015
mtps_version: v=office.15
---

# LineSeparator Property (ADO)


_**Applies to:** Access 2013 | Office 2013_

Indicates the binary character to be used as the line separator in text [Stream](stream-object-ado.md) objects.

## Settings and Return Values

Sets or returns a [LineSeparatorsEnum](lineseparatorsenum.md) value that indicates the line separator character used in the **Stream**. The default value is **adCRLF**.

## Remarks

**LineSeparator** is used to interpret lines when reading the content of a text **Stream**. Lines can be skipped with the [SkipLine](skipline-method-ado.md) method.

**LineSeparator** is used only with text **Stream** objects ([Type](type-property-ado-stream.md) is **adTypeText**). This property is ignored if **Type** is **adTypeBinary**.

