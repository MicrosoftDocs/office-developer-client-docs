---
title: MaxRecords property (ADO)
TOCTitle: MaxRecords property (ADO)
ms:assetid: 424b2d41-073a-3fbe-30aa-99fac94f9a81
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249195(v=office.15)
ms:contentKeyID: 48544475
ms.date: 09/18/2015
mtps_version: v=office.15
---

# MaxRecords property (ADO)


**Applies to**: Access 2013, Office 2013

Indicates the maximum number of records to return to a [Recordset](recordset-object-ado.md) from a query.

## Settings and return values

Sets or returns a **Long** value that indicates the maximum number of records to return. Default is zero (no limit).

## Remarks

Use the **MaxRecords** property to limit the number of records that the provider returns from the data source. The default setting of this property is zero, which means the provider returns all requested records.

The **MaxRecords** property is read/write when the **Recordset** is closed and read-only when it is open.

