---
title: SetEOS Method (ADO)
TOCTitle: SetEOS Method (ADO)
ms:assetid: d438eecf-7ab3-a07d-b6d5-8816db4aae7c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250063(v=office.15)
ms:contentKeyID: 48547933
ms.date: 09/18/2015
mtps_version: v=office.15
---

# SetEOS Method (ADO)


_**Applies to:** Access 2013 | Office 2013_

Sets the position that is the end of the stream.

## Syntax

*Stream*.SetEOS

## Remarks

**SetEOS** updates the value of the [EOS](eos-property-ado.md) property, by making the current [Position](position-property-ado.md) the end of the stream. Any bytes or characters following the current position are truncated.

Since [Write](write-method-ado.md), [WriteText](writetext-method-ado.md), and [CopyTo](copyto-method-ado.md) do not truncate any extra values in existing **Stream** objects, you can truncate these bytes or characters by setting the new end-of-stream position with **SetEOS**.


> [!WARNING]
> <P>If you set <STRONG>EOS</STRONG> to a position before the actual end of the stream, you will lose all data after the new <STRONG>EOS</STRONG> position.</P>


