---
title: WillConnect Event (ADO)
TOCTitle: WillConnect Event (ADO)
ms:assetid: 8b0e9955-4e7a-7af8-ce6c-7a4ba569a5bb
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249611(v=office.15)
ms:contentKeyID: 48546208
ms.date: 09/18/2015
mtps_version: v=office.15
---

# WillConnect Event (ADO)


**Applies to**: Access 2013 | Office 2013


The **WillConnect** event is called before a connection starts.

## Syntax

WillConnect*ConnectionString*, *UserID*, *Password*, *Options*, *adStatus*, *pConnection*

## Parameters

  - *ConnectionString*

  - A **String** that contains connection information for the pending connection.

  - *UserID*

  - A **String** that contains a user name for the pending connection.

  - *Password*

  - A **String** that contains a password for the pending connection.

  - *Options*

  - A **Long** value that indicates how the provider should evaluate the *ConnectionString*. Your only option is **adAsyncOpen**.

  - *adStatus*

  - [EventStatusEnum](eventstatusenum.md)
    
    When this event is called, this parameter is set to **adStatusOK** by default. It is set to **adStatusCantDeny** if the event cannot request cancellation of the pending operation.
    
    Before this event returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications. Set this parameter to **adStatusCancel** to request the connection operation that caused cancellation of this notification.

  - *pConnection*

  - The [Connection](connection-object-ado.md) object for which this event notification applies. Changes to the parameters of the **Connection** by the **WillConnect** event handler will have no effect on the **Connection**.

## Remarks

When **WillConnect** is called, the *ConnectionString*, *UserID*, *Password*, and *Options* parameters are set to the values established by the operation that caused this event (the pending connection), and can be changed before the event returns. **WillConnect** may return a request that the pending connection be canceled.

When this event is canceled, **ConnectComplete** will be called with its *adStatus* parameter set to **adStatusErrorsOccurred**.

