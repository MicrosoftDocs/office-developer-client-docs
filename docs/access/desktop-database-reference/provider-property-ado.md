---
title: Provider Property (ADO)
TOCTitle: Provider Property (ADO)
ms:assetid: 1b795f51-93d7-431c-b1fe-0db95f69a56a
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248953(v=office.15)
ms:contentKeyID: 48543543
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Provider Property (ADO)


**Applies to**: Access 2013, Office 2013

Indicates the name of the provider for a [Connection](connection-object-ado.md) object.

## Settings and Return Values

Sets or returns a **String** value that indicates the provider name.

## Remarks

Use the **Provider** property to set or return the name of the provider for a connection. This property can also be set by the contents of the [ConnectionString](connectionstring-property-ado.md) property or the *ConnectionString* argument of the [Open](open-method-ado-connection.md) method; however, specifying a provider in more than one place while calling the **Open** method can have unpredictable results. If no provider is specified, the property will default to MSDASQL ([Microsoft OLE DB Provider for ODBC](microsoft-ole-db-provider-for-odbc.md)).

The **Provider** property is read/write when the connection is closed and read-only when it is open. The setting does not take effect until you either open the **Connection** object or access the [Properties](properties-collection-ado.md) collection of the **Connection** object. If the setting is not valid, an error occurs.

