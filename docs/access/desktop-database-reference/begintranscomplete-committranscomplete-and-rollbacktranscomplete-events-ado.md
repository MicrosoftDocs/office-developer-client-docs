---
title: BeginTransComplete, CommitTransComplete, RollbackTransComplete events (ADO)
TOCTitle: BeginTransComplete, CommitTransComplete, and RollbackTransComplete events (ADO)
ms:assetid: 9d0ae38e-530a-7a89-a344-f3ab401c2e35
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249713(v=office.15)
ms:contentKeyID: 48546615
ms.date: 09/18/2015
mtps_version: v=office.15
---

# BeginTransComplete, CommitTransComplete, and RollbackTransComplete events (ADO)

**Applies to**: Access 2013, Office 2013

These events will be called after the associated operation on the [Connection](connection-object-ado.md) object finishes executing.

- **BeginTransComplete** is called after the [BeginTrans](begintrans-committrans-and-rollbacktrans-methods-ado.md) operation.

- **CommitTransComplete** is called after the [CommitTrans](begintrans-committrans-and-rollbacktrans-methods-ado.md) operation.

- **RollbackTransComplete** is called after the [RollbackTrans](begintrans-committrans-and-rollbacktrans-methods-ado.md) operation.

## Syntax

BeginTransComplete*TransactionLevel*, *pError*, *adStatus*, *pConnection*

CommitTransComplete*pError*, *adStatus*, *pConnection*

RollbackTransComplete*pError*, *adStatus*, *pConnection*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*TransactionLevel* |A **Long** value that contains the new transaction level of the **BeginTrans** that caused this event.|
|*pError* |An [Error](error-object-ado.md) object. It describes the error that occurred if the value of EventStatusEnum is **adStatusErrorsOccurred**; otherwise, it is not set.|
|*adStatus* |[EventStatusEnum](eventstatusenum.md). These events can prevent subsequent notifications by setting this parameter to **adStatusUnwantedEvent** before the event returns.|
|*pConnection* |The **Connection** object for which this event occurred.|

## Remarks

In Visual C++, multiple **Connections** can share the same event handling method. The method uses the returned **Connection** object to determine which object caused the event.

If the [Attributes](attributes-property-ado.md) property is set to **adXactCommitRetaining** or **adXactAbortRetaining**, a new transaction starts after committing or rolling back a transaction. Use the **BeginTransComplete** event to ignore all but the first transaction start event.

