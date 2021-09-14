---
title: QueryDef.Cancel method (DAO)
TOCTitle: Cancel Method
ms:assetid: 91e61012-c01c-4c24-185c-bdadb7f33a58
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197642(v=office.15)
ms:contentKeyID: 48546364
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1055470
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# QueryDef.Cancel method (DAO)


**Applies to**: Access 2013, Office 2013

## Syntax

*expression* .Cancel

*expression* A variable that represents a **QueryDef** object.

## Remarks

Use the **Cancel** method to terminate execution of an asynchronous **Execute** or **OpenConnection** method call (that is, the method was invoked with the dbRunAsync option). **Cancel** will return a run-time error if dbRunAsync was not used in the method you're trying to terminate.

