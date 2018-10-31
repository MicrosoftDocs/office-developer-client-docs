---
title: Recordset.MoveNext Method (DAO)
TOCTitle: MoveNext Method
ms:assetid: 0a1315cf-92f8-b8ef-1542-081e8c2d5be0
ms:mtpsurl: https://msdn.microsoft.com/library/Ff845090(v=office.15)
ms:contentKeyID: 48543142
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset.MoveNext Method (DAO)


**Applies to**: Access 2013, Office 2013

Moves to the next record in a specified **Recordset** object and make that record the current record.

## Syntax

*expression* .MoveNext

*expression* A variable that represents a **Recordset** object.

## Remarks

Use the **Move** methods to move from record to record without applying a condition.

If you edit the current record, be sure you use the **Update** method to save the changes before you move to another record. If you move to another record without updating, your changes are lost without warning.

When you open a **Recordset**, the first record is current and the **BOF** property is **False**. If the **Recordset** contains no records, the **BOF** property is **True**, and there is no current record.

If you use **MoveNext** when the last record is current, the **EOF** property is **True**, and there is no current record. If you use **MoveNext** again, an error occurs, and **EOF** remains **True**.

If recordset refers to a table-type **Recordset** (Microsoft Access workspaces only), movement follows the current index. You can set the current index by using the **Index** property. If you don't set the current index, the order of returned records is undefined.

You can't use the **MoveFirst**, **MoveLast**, and **MovePrevious** methods on a forward–only–type **Recordset** object.

To move the position of the current record in a **Recordset** object a specific number of records forward or backward, use the **Move** method.

