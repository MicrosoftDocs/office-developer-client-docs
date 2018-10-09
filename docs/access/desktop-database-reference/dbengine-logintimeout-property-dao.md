---
title: DBEngine.LoginTimeout Property (DAO)
TOCTitle: LoginTimeout Property
ms:assetid: 81d14153-79c5-7860-b6a8-4079d2d7acf7
ms:mtpsurl: https://msdn.microsoft.com/library/Ff196648(v=office.15)
ms:contentKeyID: 48545964
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1052923
f1_categories:
- Office.Version=v15
---

# DBEngine.LoginTimeout Property (DAO)


**Applies to**: Access 2013 | Office 2013

Sets or returns the number of seconds before an error occurs when you attempt to log on to an ODBC database.

## Syntax

*expression* .LoginTimeout

*expression* A variable that represents a **DBEngine** object.

## Remarks

The default **LoginTimeout** property setting is 20 seconds. When the **LoginTimeout** property is set to 0, no timeout occurs.

When you're attempting to log on to an ODBC database, such as Microsoft SQL Server, the connection can fail as a result of network errors or because the server isn't running. Rather than waiting for the default 20 seconds to connect, you can specify how long to wait before raising an error. Logging on to the server happens implicitly as part of a number of different events, such as running a query on an external server database.

