﻿---
title: TableDefs.Count Property (DAO)
TOCTitle: Count Property
ms:assetid: 6e2cf3e5-524f-a643-b1dc-99a4b2bb2e63
ms:mtpsurl: https://msdn.microsoft.com/library/Ff195561(v=office.15)
ms:contentKeyID: 48545508
ms.date: 09/18/2015
mtps_version: v=office.15
---

# TableDefs.Count Property (DAO)


**Applies to**: Access 2013 | Office 2013

Returns the number of objects in the specified collection. Read-only.

## Syntax

*expression* .Count

*expression* A variable that represents a **TableDefs** object.

## Remarks

Because members of a collection begin with 0, you should always code loops starting with the 0 member and ending with the value of the **Count** property minus 1. If you want to loop through the members of a collection without checking the **Count** property, you can use a **For Each...Next** command.

The **Count** property setting is never Null. If its value is 0, there are no objects in the collection.

