---
title: SkipLine Method (ADO)
TOCTitle: SkipLine Method (ADO)
ms:assetid: 419c24c3-6b84-eed0-5884-f2dcd485dc3d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249187(v=office.15)
ms:contentKeyID: 48544456
ms.date: 09/18/2015
mtps_version: v=office.15
---

# SkipLine Method (ADO)


**Applies to**: Access 2013, Office 2013

Skips one entire line when reading a text stream.

## Syntax

*Stream*.SkipLine

## Remarks

All characters up to, and including the next line separator, are skipped. By default, the [LineSeparator](lineseparator-property-ado.md) is **adCRLF**. If you attempt to skip past [EOS](eos-property-ado.md), the current position will simply remain at **EOS**.

The **SkipLine** method is used with text streams ([Type](type-property-ado-stream.md) is **adTypeText**).

