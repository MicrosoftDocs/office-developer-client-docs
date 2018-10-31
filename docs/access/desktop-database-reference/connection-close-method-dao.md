---
title: Connection.Close Method (DAO)
TOCTitle: Close Method
ms:assetid: 9b1a77cb-da12-24d6-892f-a56be103d51d
ms:mtpsurl: https://msdn.microsoft.com/library/Ff198015(v=office.15)
ms:contentKeyID: 48546559
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Connection.Close Method (DAO)


**Applies to**: Access 2013, Office 2013

Closes an open **Connection**.

## Syntax

*expression* .Close

*expression* A variable that represents a **Connection** object.

## Remarks

If the **Recordset** object is already closed when you use **Close**, a run-time error occurs.

If you try to close a **Connection** object while it has any open **Recordset** objects, the **Recordset** objects will be closed and any pending updates or edits will be canceled. Similarly, if you try to close a **Workspace** object while it has any open **Connection** objects, those **Connection** objects will be closed, which will close their **Recordset** objects.

An alternative to the **Close** method is to set the value of an object variable to **Nothing** (Set dbsTemp = Nothing).

