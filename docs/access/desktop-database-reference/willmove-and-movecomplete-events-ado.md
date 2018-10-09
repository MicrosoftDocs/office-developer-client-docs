---
title: WillMove and MoveComplete Events (ADO)
TOCTitle: WillMove and MoveComplete Events (ADO)
ms:assetid: fe7eb823-b388-6b3d-1ae9-056018032ef5
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250307(v=office.15)
ms:contentKeyID: 48548937
ms.date: 09/18/2015
mtps_version: v=office.15
---

# WillMove and MoveComplete Events (ADO)


**Applies to**: Access 2013 | Office 2013

The **WillMove** event is called before a pending operation changes the current position in the [Recordset](recordset-object-ado.md). The **MoveComplete** event is called after the current position in the **Recordset** changes.

## Syntax

WillMove*adReason*, *adStatus*, *pRecordset*

MoveComplete*adReason*, *pError*, *adStatus*, *pRecordset*

## Parameters

  - *adReason*

  - An [EventReasonEnum](eventreasonenum.md) value that specifies the reason for this event. Its value can be **adRsnMoveFirst**, **adRsnMoveLast**, **adRsnMoveNext**, **adRsnMovePrevious**, **adRsnMove**, or **adRsnRequery**.

  - *pError*

  - An [Error](error-object-ado.md) object. It describes the error that occurred if the value of *adStatus* is **adStatusErrorsOccurred**; otherwise it is not set.

  - *adStatus*

  - [EventStatusEnum](eventstatusenum.md)
    
    When **WillMove** is called, this parameter is set to **adStatusOK** if the operation that caused the event was successful. It is set to **adStatusCantDeny** if this event cannot request cancellation of the pending operation.
    
    When **MoveComplete** is called, this parameter is set to **adStatusOK** if the operation that caused the event was successful, or to **adStatusErrorsOccurred** if the operation failed.
    
    Before **WillMove** returns, set this parameter to **adStatusCancel** to request cancellation of the pending operation or set this parameter to adStatusUnwantedEvent to prevent subsequent notications.
    
    Before **MoveComplete** returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications.

  - *pRecordset*

  - A [Recordset](recordset-object-ado.md) object. The **Recordset** for which this event occurred.

## Remarks

A **WillMove** or **MoveComplete** event may occur due to the following **Recordset** operations: [Open](open-method-ado-recordset.md), [Move](move-method-ado.md), [MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MovePrevious](movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [AddNew](addnew-method-ado.md), and [Requery](requery-method-ado.md). These events may occur because of the following properties: [Filter](filter-property-ado.md), [Index](index-property-ado.md), [Bookmark](bookmark-property-ado.md), [AbsolutePage](absolutepage-property-ado.md), and [AbsolutePosition](absoluteposition-property-ado.md). These events also occur if a child **Recordset** has **Recordset** events connected and the parent **Recordset** is moved.

You must set the **adStatus** parameter to **adStatusUnwantedEvent** for each possible adReason value in order to completely stop event notification for any event that includes an adReason parameter.

