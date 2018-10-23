---
title: ConnectionTimeout Property (ADO)
TOCTitle: ConnectionTimeout Property (ADO)
ms:assetid: efc39fd8-afce-5ac0-2fff-cbb55c1a444d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250218(v=office.15)
ms:contentKeyID: 48548589
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ConnectionTimeout Property (ADO)


**Applies to**: Access 2013, Office 2013

Indicates how long to wait while establishing a connection before terminating the attempt and generating an error.

## Settings and Return Values

Sets or returns a **Long** value that indicates, in seconds, how long to wait for the connection to open. Default is 15.

## Remarks

Use the **ConnectionTimeout** property on a [Connection](connection-object-ado.md) object if delays from network traffic or heavy server use make it necessary to abandon a connection attempt. If the time from the **ConnectionTimeout** property setting elapses prior to the opening of the connection, an error occurs and ADO cancels the attempt. If you set the property to zero, ADO will wait indefinitely until the connection is opened. Make sure the provider to which you are writing code supports the **ConnectionTimeout** functionality.

The **ConnectionTimeout** property is read/write when the connection is closed and read-only when it is open.

