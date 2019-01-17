---
title: QueryDef.Close method (DAO)
TOCTitle: Close Method
ms:assetid: b2b63462-453d-9e2b-0bb3-69a4a7a6ecef
ms:mtpsurl: https://msdn.microsoft.com/library/Ff822031(v=office.15)
ms:contentKeyID: 48547179
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1052976
f1_categories:
- Office.Version=v15
localization_priority: Normal
---

# QueryDef.Close method (DAO)


**Applies to**: Access 2013, Office 2013

Closes an open **QueryDef**.

## Syntax

*expression* .Close

*expression* A variable that represents a **QueryDef** object.

## Remarks

If the **QueryDef** object is already closed when you use **Close**, a run-time error occurs.

An alternative to the **Close** method is to set the value of an object variable to **Nothing** (Set dbsTemp = Nothing).

