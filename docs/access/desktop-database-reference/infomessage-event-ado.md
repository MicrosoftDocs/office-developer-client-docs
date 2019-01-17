---
title: InfoMessage event (ADO)
TOCTitle: InfoMessage event (ADO)
ms:assetid: 5d4f487f-96c8-4cf6-60ab-583510d3096f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249328(v=office.15)
ms:contentKeyID: 48545109
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# InfoMessage event (ADO)

**Applies to**: Access 2013, Office 2013

The **InfoMessage** event is called whenever a warning occurs during a **ConnectionEvent** operation.

## Syntax

InfoMessage*pError*, *adStatus*, *pConnection*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*pError* |An [Error](error-object-ado.md) object. This parameter contains any errors that are returned. If multiple errors are returned, enumerate the **Errors** collection to find them.|
|*adStatus* |[EventStatusEnum](eventstatusenum.md). Before this event returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications.|
|*pConnection* |A [Connection](connection-object-ado.md) object. The connection for which the warning occurred. For example, warnings can occur when opening a **Connection** object or executing a [Command](command-object-ado.md) on a **Connection**.|

