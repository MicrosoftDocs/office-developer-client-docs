---
title: Workspace.Close method (DAO)
TOCTitle: Close Method
ms:assetid: 9b3d28f9-5cde-0dd9-8a4a-d2efaec5fe5d
ms:mtpsurl: https://msdn.microsoft.com/library/Ff198027(v=office.15)
ms:contentKeyID: 48546565
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Workspace.Close method (DAO)


**Applies to**: Access 2013, Office 2013

Closes an open **Workspace**.

## Syntax

*expression* .Close

*expression* A variable that represents a **Workspace** object.

## Remarks

If the **Workspace** object is already closed when you use **Close**, a run-time error occurs.

An alternative to the **Close** method is to set the value of an object variable to **Nothing** (Set dbsTemp = Nothing).

