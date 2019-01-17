---
title: Errors.Count property (DAO)
TOCTitle: Count Property
ms:assetid: ad135955-3b18-4f99-66d9-aff1492df13b
ms:mtpsurl: https://msdn.microsoft.com/library/Ff821719(v=office.15)
ms:contentKeyID: 48547028
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# Errors.Count property (DAO)


**Applies to**: Access 2013, Office 2013

Returns the number of objects in the specified collection. Read-only.

## Syntax

*expression* .Count

*expression* A variable that represents an **Errors** object.

## Remarks

Because members of a collection begin with 0, you should always code loops starting with the 0 member and ending with the value of the **Count** property minus 1. If you want to loop through the members of a collection without checking the **Count** property, you can use a **For Each...Next** command.

The **Count** property setting is never Null. If its value is 0, there are no objects in the collection.

