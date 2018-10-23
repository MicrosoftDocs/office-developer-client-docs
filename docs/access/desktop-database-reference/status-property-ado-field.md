---
title: Status Property (ADO Field)
TOCTitle: Status Property (ADO Field)
ms:assetid: 7a7b45e8-2934-2e8e-77fa-a4f38272548d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249507(v=office.15)
ms:contentKeyID: 48545795
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Status Property (ADO Field)


**Applies to**: Access 2013, Office 2013

Indicates the status of a [Field](field-object-ado.md) object.

## Return Value

Returns a [FieldStatusEnum](fieldstatusenum.md) value. The default value is **adFieldOK**.

## Remarks

This property always returns **adFieldOK** for fields of a [Recordset](recordset-object-ado.md) object.

Additions and deletions to the [Fields](fields-collection-ado.md) collections of the [Record](record-object-ado.md) object are cached until the [Update](update-method-ado.md) method is called. The **Status** property enables you to determine which fields have been successfully added or deleted.

To enhance performance, schema changes are cached until **Update** is called, and then the changes are made in a batch optimistic update. If the **Update** method is not called, the server is not updated. If any updates fail then an error is returned and the **Status** property indicates the combined values of the operation and error status code. For example, **adFieldPendingInsert** **OR** **adFieldPermissionDenied**. The **Status** property for each **Field** can be used to determine why the **Field** was not added, modified, or deleted. **Status** is only meaningfully exposed on the **Record**.**Fields** collection and not the **Recordset**.**Fields** collection.

Two problems can arise when adding, modifying, or deleting a **Field**. If the user deletes a **Field**, it is marked for deletion from the **Fields** collection. If the subsequent **Update** returns an error because the user tried to delete a **Field** for which they do not have permission, the **Field** will have a status of **adFieldPermissionDenied** **OR** **adFieldPendingDelete**. Calling the [CancelUpdate](cancelupdate-method-ado.md) method restores original values and sets the **Status** to **adFieldOK**. Similarly, the **Update** method may return an error because a new **Field** was added and given an inappropriate value. In that case the new **Field** will be in the **Fields** collection and have a status of **adFieldPendingInsert** and perhaps **adFieldCantCreate**. You can supply an appropriate value for the new **Field** and call **Update** again. Note that calling **Resync** instead requeries the provider.

