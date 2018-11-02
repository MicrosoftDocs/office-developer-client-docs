---
title: Documents.Count property (DAO)
TOCTitle: Count Property
ms:assetid: 3fc0b1e6-f7be-cd43-711f-5cf5763fe7f6
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192858(v=office.15)
ms:contentKeyID: 48544407
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1053325
f1_categories:
- Office.Version=v15
---

# Documents.Count property (DAO)


**Applies to**: Access 2013, Office 2013

Returns the number of objects in the specified collection. Read-only.

## Syntax

*expression* .Count

*expression* A variable that represents a **Documents** object.

## Remarks

Because members of a collection begin with 0, you should always code loops starting with the 0 member and ending with the value of the **Count** property minus 1. If you want to loop through the members of a collection without checking the **Count** property, you can use a **For Each...Next** command.

The **Count** property setting is never Null. If its value is 0, there are no objects in the collection.

