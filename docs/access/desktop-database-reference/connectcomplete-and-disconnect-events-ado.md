---
title: ConnectComplete and Disconnect Events (ADO)
TOCTitle: ConnectComplete and Disconnect Events (ADO)
ms:assetid: 8ecb080b-7fc9-7565-25bd-bd57b983750d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249629(v=office.15)
ms:contentKeyID: 48546293
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ConnectComplete and Disconnect Events (ADO)


**Applies to**: Access 2013, Office 2013

The **ConnectComplete** event is called after a connection *starts*. The **Disconnect** event is called after a connection *ends*.

## Syntax

ConnectComplete*pError*, *adStatus*, *pConnection*

Disconnect*adStatus*, *pConnection*

## Parameters

  - *pError*

  - An [Error](error-object-ado.md) object. It describes the error that occurred if the value of *adStatus* is **adStatusErrorsOccurred**; otherwise it is not set.

  - *adStatus*

  - [EventStatusEnum](eventstatusenum.md)
    
    When **ConnectComplete** is called, this parameter is set to **adStatusCancel** if a **WillConnect** event has requested cancellation of the pending connection.
    
    Before either event returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications. However, closing and reopening the [Connection](connection-object-ado.md) causes these events to occur again.

  - *pConnection*

  - The **Connection** object for which this event applies.

