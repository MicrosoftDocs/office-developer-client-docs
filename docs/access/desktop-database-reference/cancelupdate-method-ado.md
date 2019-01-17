---
title: CancelUpdate method (ADO)
TOCTitle: CancelUpdate method (ADO)
ms:assetid: 2bd4d168-ba52-7786-5046-44febeda88e1
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249065(v=office.15)
ms:contentKeyID: 48543938
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# CancelUpdate method (ADO)


**Applies to**: Access 2013, Office 2013

Cancels any changes made to the current or new row of a [Recordset](recordset-object-ado.md) object, or the [Fields](fields-collection-ado.md) collection of a [Record](record-object-ado.md) object, before calling the [Update](update-method-ado.md) method.

## Syntax

*recordset*.CancelUpdate

*record*.*Fields*.CancelUpdate

## Remarks

**Recordset**

Use the **CancelUpdate** method to cancel any changes made to the current row or to discard a newly added row. You cannot cancel changes to the current row or a new row after you call the **Update** method, unless the changes are either part of a transaction that you can roll back with the [RollbackTrans](begintrans-committrans-and-rollbacktrans-methods-ado.md) method, or part of a batch update. In the case of a batch update, you can cancel the **Update** with the **CancelUpdate** or [CancelBatch](cancelbatch-method-ado.md) method.

If you are adding a new row when you call the **CancelUpdate** method, the current row becomes the row that was current before the [AddNew](addnew-method-ado.md) call.

If you are in edit mode and want to move off the current record (for example, with [Move](move-method-ado.md), [NextRecordset](nextrecordset-method-ado.md), or [Close](close-method-ado.md)), you can use **CancelUpdate** to cancel any pending changes. You may need to do this if the update cannot successfully be posted to the data source (for example, an attempted delete that fails due to referential integrity violations will leave the **Recordset** in edit mode after a call to [Delete](delete-method-ado-recordset.md)).

**Record**

The **CancelUpdate** method cancels any pending insertions or deletions of [Field](field-object-ado.md) objects, and cancels pending updates of existing fields and restores them to their original values. The [Status](status-property-ado-recordset.md) property of all fields in the **Fields** collection is set to **adFieldOK**.

