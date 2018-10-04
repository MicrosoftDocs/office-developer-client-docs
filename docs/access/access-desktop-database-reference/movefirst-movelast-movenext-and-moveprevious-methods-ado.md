﻿---
title: MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (ADO)
TOCTitle: MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (ADO)
ms:assetid: d04ce41c-77c9-df42-115a-65c50a38518a
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250039(v=office.15)
ms:contentKeyID: 48547836
ms.date: 09/18/2015
mtps_version: v=office.15
---

# MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (ADO)


**Applies to**: Access 2013 | Office 2013

Moves to the first, last, next, or previous record in a specified [Recordset](recordset-object-ado.md) object and makes that record the current record.

## Syntax

*recordset*.{ MoveFirst | MoveLast | MoveNext | MovePrevious}

## Remarks

Use the **MoveFirst** method to move the current record position to the first record in the **Recordset**.

Use the **MoveLast** method to move the current record position to the last record in the **Recordset**. The **Recordset** object must support bookmarks or backward cursor movement; otherwise, the method call will generate an error.

A call to either **MoveFirst** or **MoveLast** when the **Recordset** is empty (both **BOF** and **EOF** are True) generates an error.

Use the **MoveNext** method to move the current record position one record forward (toward the bottom of the **Recordset**). If the last record is the current record and you call the **MoveNext** method, ADO sets the current record to the position after the last record in the **Recordset** ([EOF](bof-eof-properties-ado.md) is **True**). An attempt to move forward when the **EOF** property is already **True** generates an error.

In cases where the **Recordset** has been filtered or sorted and the current record's data is changed, the position may also change. In such cases the **MoveNext** method works normally, but you should be aware that the position is moved one record forward from the new position, not the old position. For example, changing the data in the current record, such that the record is moved to the end of the sorted **Recordset,** would mean that calling **MoveNext** results in ADO setting the current record to the position after the last record in the **Recordset** (**EOF** = **True**).

Use the **MovePrevious** method to move the current record position one record backward (toward the top of the **Recordset**). The **Recordset** object must support bookmarks or backward cursor movement; otherwise, the method call will generate an error. If the first record is the current record and you call the **MovePrevious** method, ADO sets the current record to the position before the first record in the **Recordset** ([BOF](bof-eof-properties-ado.md) is **True**). An attempt to move backward when the **BOF** property is already **True** generates an error. If the **Recordset** object does not support either bookmarks or backward cursor movement, the **MovePrevious** method will generate an error.

If the **Recordset** is forward only and you want to support both forward and backward scrolling, you can use the [CacheSize](cachesize-property-ado.md) property to create a record cache that will support backward cursor movement through the [Move](move-method-ado.md) method. Because cached records are loaded into memory, you should avoid caching more records than is necessary. You can call the **MoveFirst** method in a forward-only **Recordset** object; doing so may cause the provider to re-execute the command that generated the **Recordset** object.

