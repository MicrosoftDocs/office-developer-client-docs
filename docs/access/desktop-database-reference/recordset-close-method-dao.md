---
title: Recordset.Close method (DAO)
TOCTitle: Close Method
ms:assetid: e76a81c6-ca0d-e310-c1dc-cbc5d6f6248b
ms:mtpsurl: https://msdn.microsoft.com/library/Ff836011(v=office.15)
ms:contentKeyID: 48548404
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: high
---

# Recordset.Close method (DAO)


**Applies to**: Access 2013, Office 2013

Closes an open **Recordset**.

## Syntax

*expression* .Close

*expression* A variable that represents a **Recordset** object.

## Remarks

If the **Recordset** object is already closed when you use **Close**, a run-time error occurs.

If you try to close a **Connection** object while it has any open **Recordset** objects, the **Recordset** objects will be closed and any pending updates or edits will be canceled. Similarly, if you try to close a **Workspace** object while it has any open **Connection** objects, those **Connection** objects will be closed, which will close their **Recordset** objects.

An alternative to the **Close** method is to set the value of an object variable to **Nothing** (Set dbsTemp = Nothing).

