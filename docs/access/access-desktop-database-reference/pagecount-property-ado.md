---
title: PageCount Property (ADO)
TOCTitle: PageCount Property (ADO)
ms:assetid: 9cd8bf5c-b1e7-a453-4629-9cba7e408f53
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249712(v=office.15)
ms:contentKeyID: 48546609
ms.date: 09/18/2015
mtps_version: v=office.15
---

# PageCount Property (ADO)


**Applies to**: Access 2013 | Office 2013

Indicates how many pages of data the [Recordset](recordset-object-ado.md) object contains.

## Return Value

Returns a **Long** value that indicates the number of pages in the **Recordset**.

## Remarks

Use the **PageCount** property to determine how many pages of data are in the **Recordset** object. *Pages* are groups of records whose size equals the [PageSize](pagesize-property-ado.md) property setting. Even if the last page is incomplete because there are fewer records than the **PageSize** value, it counts as an additional page in the **PageCount** value. If the **Recordset** object does not support this property, the value will be -1 to indicate that the **PageCount** is indeterminable.

See the **PageSize** and [AbsolutePage](absolutepage-property-ado.md) properties for more on page functionality.

