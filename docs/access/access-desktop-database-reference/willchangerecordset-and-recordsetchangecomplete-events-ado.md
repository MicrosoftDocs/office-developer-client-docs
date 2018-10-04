---
title: WillChangeRecordset and RecordsetChangeComplete Events (ADO)
TOCTitle: WillChangeRecordset and RecordsetChangeComplete Events (ADO)
ms:assetid: 2cec4cf9-a4e9-c386-5202-04e86f4cf8ad
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249068(v=office.15)
ms:contentKeyID: 48543963
ms.date: 09/18/2015
mtps_version: v=office.15
---

# WillChangeRecordset and RecordsetChangeComplete Events (ADO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Parameters  
Remarks  

The **WillChangeRecordset** event is called before a pending operation changes the [Recordset](recordset-object-ado.md). The **RecordsetChangeComplete** event is called after the **Recordset** has changed.

## Syntax

WillChangeRecordset*adReason*, *adStatus*, *pRecordset*

RecordsetChangeComplete*adReason*, *pError*, *adStatus*, *pRecordset*

## Parameters

  - *adReason*

  - An [EventReasonEnum](eventreasonenum.md) value that specifies the reason for this event. Its value can be **adRsnRequery**, **adRsnResynch**, **adRsnClose**, **adRsnOpen**.

  - *adStatus*

  - [EventStatusEnum](eventstatusenum.md)
    
    When **WillChangeRecordset** is called, this parameter is set to **adStatusOK** if the operation that caused the event was successful. It is set to **adStatusCantDeny** if this event cannot request cancellation of the pending operation.
    
    When **RecordsetChangeComplete** is called, this parameter is set to **adStatusOK** if the operation that caused the event was successful, **adStatusErrorsOccurred** if the operation failed, or **adStatusCancel** if the operation associated with the previously accepted **WillChangeRecordset** event has been canceled.
    
    Before **WillChangeRecordset** returns, set this parameter to **adStatusCancel** to request cancellation of the pending operation or set this parameter to adStatusUnwantedEvent to prevent subsequent notifications.
    
    Before **WillChangeRecordset** or **RecordsetChangeComplete** returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications.

  - *pError*

  - An [Error](error-object-ado.md) object. It describes the error that occurred if the value of *adStatus* is **adStatusErrorsOccurred**; otherwise it is not set.

  - *pRecordset*

  - A **Recordset** object. The **Recordset** for which this event occurred.

## Remarks

A **WillChangeRecordset** or **RecordsetChangeComplete** event may occur due to the **Recordset** [Requery](requery-method-ado.md) or [Open](open-method-ado-recordset.md) methods.

If the provider does not support bookmarks, a **RecordsetChange** event notification occurs each time new rows are retrieved from the provider. The frequency of this event depends on the **RecordsetCacheSize** property.

You must set the **adStatus** parameter to **adStatusUnwantedEvent** for each possible **adReason** value in order to completely stop event notification for any event that includes an **adReason** parameter.

