﻿---
title: Command Object Overview
TOCTitle: Command Object Overview
ms:assetid: 3d6d81c4-4cf0-0c13-adb3-0c2c5934dc21
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249166(v=office.15)
ms:contentKeyID: 48544346
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Command Object Overview


**Applies to**: Access 2013 | Office 2013

With the collections, methods, and properties of a **Command** object, you can do the following:

  - Define the executable text of the command (for example, a SQL statement or a stored procedure) by using the **CommandText** property.

  - Define parameterized queries or stored procedure arguments by using **Parameter** objects and the **Parameters** collection.

  - Execute a command and return a **Recordset** object, if appropriate, by using the **Execute** method.

  - Specify the type of command by using the **CommandType** property prior to execution to optimize performance.

  - Control whether the provider saves a prepared (or compiled) version of the command prior to execution by using the **Prepared** property.

  - Set the number of seconds that a provider will wait for a command to execute by using the **CommandTimeout** property.

  - Associate an open connection with a **Command** object by setting its **ActiveConnection** property.

  - Set the **Name** property to identify the **Command** object as a method on the associated **Connection** object.

  - Pass a **Command** object to the **Source** property of a **Recordset** in order to obtain data.

