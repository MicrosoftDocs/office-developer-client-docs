---
title: Update Resync Property--Dynamic (ADO)
TOCTitle: Update Resync Property--Dynamic (ADO)
ms:assetid: 0af9cfd2-8042-65c9-cec6-77d2e7a88ad9
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248842(v=office.15)
ms:contentKeyID: 48543166
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Update Resync Property--Dynamic (ADO)


**Applies to**: Access 2013, Office 2013

Specifies whether the [UpdateBatch](updatebatch-method-ado.md) method is followed by an implicit [Resync](resync-method-ado.md) method operation, and if so, the scope of that operation.

## Settings and Return Values

Sets or returns one or more of the [ADCPROP\_UPDATERESYNC\_ENUM](adcprop-updateresync-enum.md) values.

## Remarks

The values of ADCPROP\_UPDATERESYNC\_ENUM may be combined, except for adResyncAll which already represents the combination of the rest of the values.

The constant **adResyncConflicts** stores the resync values as underlying values, but does not override pending changes.

**Update Resync** is a dynamic property appended to the [Recordset](recordset-object-ado.md) object [Properties](properties-collection-ado.md) collection when the [CursorLocation](cursorlocation-property-ado.md) property is set to **adUseClient**.

