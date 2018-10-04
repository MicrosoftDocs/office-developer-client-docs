---
title: TableDef.RecordCount Property (DAO)
TOCTitle: RecordCount Property
ms:assetid: f8804244-0134-fc1f-1f5f-4971afe17974
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff836946(v=office.15)
ms:contentKeyID: 48548783
ms.date: 09/18/2015
mtps_version: v=office.15
---

# TableDef.RecordCount Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

Returns the total number of records in a **[TableDef](tabledef-object-dao.md)** object. Read-only **Long**.

## Syntax

*expression* .RecordCount

*expression* A variable that represents a **TableDef** object.

## Remarks

A **Recordset** or **TableDef** object with no records has a **RecordCount** property setting of 0.

When you work with linked**TableDef** objects, the **RecordCount** property setting is always –1.

