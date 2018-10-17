---
<<<<<<< HEAD
title: Sort Property (ADO)
TOCTitle: Sort Property (ADO)
=======
title: Sort property (ADO)
TOCTitle: Sort property (ADO)
>>>>>>> master
ms:assetid: f2a39b7f-8b96-cd1a-8248-71f8b867454a
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250230(v=office.15)
ms:contentKeyID: 48548652
ms.date: 09/18/2015
mtps_version: v=office.15
---

<<<<<<< HEAD
# Sort Property (ADO)
=======
# Sort property (ADO)
>>>>>>> master


**Applies to**: Access 2013 | Office 2013

Indicates one or more field names on which the [Recordset](recordset-object-ado.md) is sorted, and whether each field is sorted in ascending or descending order.

<<<<<<< HEAD
## Settings and Return Values
=======
## Settings and return values
>>>>>>> master

Sets or returns a **String** value that indicates the field names in the **Recordset** on which to sort. Each name is separated by a comma, and is optionally followed by a blank and the keyword, **ASC**, which sorts the field in ascending order, or **DESC**, which sorts the field in descending order. By default, if no keyword is specified, the field is sorted in ascending order.

## Remarks

This property requires the [CursorLocation](cursorlocation-property-ado.md) property to be set to **adUseClient**. A temporary index will be created for each field specified in the **Sort** property if an index does not already exist.

The sort operation is efficient because data is not physically rearranged, but is simply accessed in the order specified by the index.

Setting the **Sort** property to an empty string will reset the rows to their original order and delete temporary indexes. Existing indexes will not be deleted.

Suppose a **Recordset** contains three fields named *firstName*, *middleInitial*, and *lastName*. Set the **Sort** property to the string, "lastName DESC, firstName ASC", which will order the **Recordset** by last name in descending order, then by first name in ascending order. The middle initial is ignored.

No field can be named "ASC" or "DESC" because those names conflict with the keywords **ASC** and **DESC**. Give a field with a conflicting name an alias by using the **AS** keyword in the query that returns the **Recordset**.

