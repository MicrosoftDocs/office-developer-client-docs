---
title: Recordset2.Cancel Method (DAO)
TOCTitle: Cancel Method
ms:assetid: cae49f36-3aad-80d8-c15f-a7a584aa2e9b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff834366(v=office.15)
ms:contentKeyID: 48547703
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset2.Cancel Method (DAO)


_**Applies to:** Access 2013 | Office 2013_

## Syntax

*expression* .Cancel

*expression* An expression that returns a **Recordset2** object.

## Remarks

Use the **Cancel** method to terminate execution of an asynchronous **Execute** or **OpenConnection** method call (that is, the method was invoked with the dbRunAsync option). **Cancel** will return a run-time error if dbRunAsync was not used in the method you're trying to terminate.

