---
title: FetchComplete event (ADO)
TOCTitle: FetchComplete event (ADO)
ms:assetid: 4863d5b5-7d77-bdef-c511-f85c9e6dec9d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249224(v=office.15)
ms:contentKeyID: 48544621
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# FetchComplete event (ADO)

**Applies to**: Access 2013, Office 2013

The **FetchComplete** event is called after all the records in a lengthy asynchronous operation have been retrieved into the [Recordset](recordset-object-ado.md).

## Syntax

FetchComplete*pError*, *adStatus*, *pRecordset*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*pError* |An [Error](error-object-ado.md) object. It describes the error that occurred if the value of **adStatus** is **adStatusErrorsOccurred**; otherwise it is not set.|
|*adStatus* |[EventStatusEnum](eventstatusenum.md). Before this event returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications.|
|*pRecordset* |A **Recordset** object. The object for which the records were retrieved.|

## Remarks

To use **FetchComplete** with Microsoft Visual Basic, Visual Basic 6.0 or later is required.

