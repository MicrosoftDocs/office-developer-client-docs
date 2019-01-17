---
title: WillChangeField and FieldChangeComplete events (ADO)
TOCTitle: WillChangeField and FieldChangeComplete events (ADO)
ms:assetid: bc4455a6-2925-33dc-d04f-8ea570e5e370
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249904(v=office.15)
ms:contentKeyID: 48547407
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# WillChangeField and FieldChangeComplete events (ADO)

**Applies to**: Access 2013, Office 2013

The **WillChangeField** event is called before a pending operation changes the value of one or more [Field](field-object-ado.md) objects in the [Recordset](recordset-object-ado.md). The **FieldChangeComplete** event is called after the value of one or more **Field** objects has changed.

## Syntax

WillChangeField*cFields*, *Fields*, *adStatus*, *pRecordset*

FieldChangeComplete*cFields*, *Fields*, *pError*, *adStatus*, *pRecordset*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*cFields* |A **Long** that indicates the number of **Field** objects in *Fields*.|
|*Fields* |For **WillChangeField**, the *Fields* parameter is an array of **Variants** that contains **Field** objects with the original values. <br/><br/>For **FieldChangeComplete**, the *Fields* parameter is an array of **Variants** that contains **Field** objects with the changed values.|
|*pError* |An [Error](error-object-ado.md) object. It describes the error that occurred if the value of *adStatus* is **adStatusErrorsOccurred**; otherwise it is not set.|
|*adStatus* |[EventStatusEnum](eventstatusenum.md). When **WillChangeField** is called, this parameter is set to **adStatusOK** if the operation that caused the event was successful. It is set to **adStatusCantDeny** if this event cannot request cancellation of the pending operation. <br/><br/>When **FieldChangeComplete** is called, this parameter is set to **adStatusOK** if the operation that caused the event was successful, or to **adStatusErrorsOccurred** if the operation failed. <br/><br/>Before **WillChangeField** returns, set this parameter to **adStatusCancel** to request cancellation of the pending operation. <br/><br/>Before **FieldChangeComplete** returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications.|
|*pRecordset* |A **Recordset** object. The **Recordset** for which this event occurred.|

## Remarks

A **WillChangeField** or **FieldChangeComplete** event may occur when setting the [Value](value-property-ado.md) property and calling the [Update](update-method-ado.md) method with field and value array parameters.

