---
title: TableDef.Updatable Property (DAO)
TOCTitle: Updatable Property
ms:assetid: 0b1ae7e5-416d-06f0-5d74-989c6db67ff2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff845128(v=office.15)
ms:contentKeyID: 48543168
ms.date: 09/18/2015
mtps_version: v=office.15
---

# TableDef.Updatable Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

Returns a value that indicates whether you can change a DAO object. Read-only **Boolean**.

## Syntax

*expression* .Updatable

*expression* A variable that represents a **TableDef** object.

## Remarks

The **Updatable** property setting is always **True** for a newly created **TableDef** object and **False** for a linked **TableDef** object. A new **TableDef** object can be appended only to a database for which the current user has write permission.

