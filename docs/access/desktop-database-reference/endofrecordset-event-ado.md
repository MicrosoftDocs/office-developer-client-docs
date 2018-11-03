---
title: EndOfRecordset event (ADO)
TOCTitle: EndOfRecordset event (ADO)
ms:assetid: 8995b851-dff6-2525-1d62-a2cfb4f95393
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249603(v=office.15)
ms:contentKeyID: 48546167
ms.date: 09/18/2015
mtps_version: v=office.15
---

# EndOfRecordset event (ADO)

**Applies to**: Access 2013, Office 2013

The **EndOfRecordset** event is called when there is an attempt to move to a row past the end of the [Recordset](recordset-object-ado.md).

## Syntax

EndOfRecordset*fMoreData*, *adStatus*, *pRecordset*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*fMoreData* |A **VARIANT\_BOOL** value that, if set to VARIANT\_TRUE, indicates more rows have been added to the **Recordset**.|
|*adStatus* |[EventStatusEnum](eventstatusenum.md). When **EndOfRecordset** is called, this parameter is set to **adStatusOK** if the operation that caused the event was successful. It is set to **adStatusCantDeny** if this event cannot request cancellation of the operation that caused this event.<br/><br/>Before **EndOfRecordset** returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications.|
|*pRecordset* | A **Recordset** object. The **Recordset** for which this event occurred.|

## Remarks

An **EndOfRecordset** event may occur if the [MoveNext](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) operation fails.

This event handler is called when an attempt is made to move past the end of the **Recordset** object, perhaps as a result of calling **MoveNext**. However, while in this event, you could retrieve more records from a database and append them to the end of the **Recordset**. In that case, set *fMoreData* to VARIANT\_TRUE, and return from **EndOfRecordset**. Then call **MoveNext** again to access the newly retrieved records.

