---
title: Database.Close method (DAO)
TOCTitle: Close Method
ms:assetid: b777ee92-172a-3342-31fc-76e7361c47fd
ms:mtpsurl: https://msdn.microsoft.com/library/Ff822418(v=office.15)
ms:contentKeyID: 48547296
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Database.Close method (DAO)


**Applies to**: Access 2013, Office 2013

Closes an open **Database**.

## Syntax

*expression* .Close

*expression* A variable that represents a **Database** object.

## Remarks

If the **Database** object is already closed when you use **Close**, a run-time error occurs.

An alternative to the **Close** method is to set the value of an object variable to **Nothing** (Set dbsTemp = Nothing).

