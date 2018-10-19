---
title: UnderlyingValue property (ADO)
TOCTitle: UnderlyingValue property (ADO)
ms:assetid: f84f4c1c-2bd4-a725-3575-ed063ead13c8
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250262(v=office.15)
ms:contentKeyID: 48548782
ms.date: 09/18/2015
mtps_version: v=office.15
---

# UnderlyingValue property (ADO)


**Applies to**: Access 2013, Office 2013



Indicates a [Field](field-object-ado.md) object's current value in the database.

## Return value

Returns a **Variant** value that indicates the value of the **Field**.

## Remarks

Use the **UnderlyingValue** property to return the current field value from the database. The field value in the **UnderlyingValue** property is the value that is visible to your transaction and may be the result of a recent update by another transaction. This may differ from the [OriginalValue](originalvalue-property-ado.md) property, which reflects the value that was originally returned to the [Recordset](recordset-object-ado.md).

This is similar to using the [Resync](resync-method-ado.md) method, but the **UnderlyingValue** property returns only the value for a specific field from the current record. This is the same value that the [Resync](resync-method-ado.md) method uses to replace the [Value](value-property-ado.md) property.

When you use this property with the **OriginalValue** property, you can resolve conflicts that arise from batch updates.

## Record

For [Record](record-object-ado.md) objects, this property will be empty for fields added before [Update](update-method-ado.md) is called.

