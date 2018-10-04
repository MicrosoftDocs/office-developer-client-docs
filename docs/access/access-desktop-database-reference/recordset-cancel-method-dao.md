---
title: Recordset.Cancel Method (DAO)
TOCTitle: Cancel Method
ms:assetid: 89acfbf1-b937-dc19-ada1-6f8f50489147
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff197080(v=office.15)
ms:contentKeyID: 48546169
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset.Cancel Method (DAO)


_**Applies to:** Access 2013 | Office 2013_

## Syntax

*expression* .Cancel

*expression* A variable that represents a **Recordset** object.

## Remarks

Use the **Cancel** method to terminate execution of an asynchronous **Execute** or **OpenConnection** method call (that is, the method was invoked with the dbRunAsync option). **Cancel** will return a run-time error if dbRunAsync was not used in the method you're trying to terminate.

