---
title: Parent Property (ADO MD)
TOCTitle: Parent Property (ADO MD)
ms:assetid: 62649da7-d35f-f11f-674c-28ce95abaf20
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249370(v=office.15)
ms:contentKeyID: 48545238
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Parent Property (ADO MD)


**Applies to**: Access 2013 | Office 2013

Indicates the member that is the parent of the current member in a hierarchy.

## Return Values

Returns a [Member](member-object-ado-md.md) object and is read-only.

## Remarks

A member that is at the top level of a hierarchy (the root) has no parent. This property is supported only on **Member** objects belonging to a [Level](level-object-ado-md.md) object. An error occurs when this property is referenced from **Member** objects belonging to a [Position](position-object-ado-md.md) object.

