---
title: QueryDef.Updatable Property (DAO)
TOCTitle: Updatable Property
ms:assetid: 9b978b7d-1d76-ff27-a032-dd94660fb088
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff198056(v=office.15)
ms:contentKeyID: 48546575
ms.date: 09/18/2015
mtps_version: v=office.15
---

# QueryDef.Updatable Property (DAO)


**Applies to**: Access 2013 | Office 2013

Returns a value that indicates whether you can change a DAO object. Read-only **Boolean**.

## Syntax

*expression* .Updatable

*expression* A variable that represents a **QueryDef** object.

## Remarks

The **Updatable** property of a **QueryDef** object is set to **True** if the query definition can be updated, even if the resulting **[Recordset](recordset-object-dao.md)** object isn't updatable.

