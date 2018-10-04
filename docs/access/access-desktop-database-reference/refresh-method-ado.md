---
title: Refresh Method (ADO)
TOCTitle: Refresh Method (ADO)
ms:assetid: f1c8829f-9c7d-12b6-7470-727ff38d663e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250227(v=office.15)
ms:contentKeyID: 48548631
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Refresh Method (ADO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Parameters  

Updates the objects in a collection to reflect objects available from, and specific to, the provider.

## Syntax

*collection*.Refresh

## Remarks

The **Refresh** method accomplishes different tasks depending on the collection from which you call it.

## Parameters

Using the **Refresh** method on a [Command](command-object-ado.md) object's [Parameters](parameters-collection-ado.md) collection retrieves provider-side parameter information for the stored procedure or parameterized query specified in the **Command** object. The collection will be empty for providers that do not support stored procedure calls or parameterized queries.

You should set the [ActiveConnection](activeconnection-property-ado.md) property of the **Command** object to a valid [Connection](connection-object-ado.md) object, the [CommandText](commandtext-property-ado.md) property to a valid command, and the [CommandType](commandtype-property-ado.md) property to **adCmdStoredProc** before calling the **Refresh** method.

If you access the **Parameters** collection before calling the **Refresh** method, ADO will automatically call the method and populate the collection for you.


> [!NOTE]
> <P>If you use the <STRONG>Refresh</STRONG> method to obtain parameter information from the provider and it returns one or more variable-length data type <A href="parameter-object-ado.md">Parameter</A> objects, ADO may allocate memory for the parameters based on their maximum potential size, which will cause an error during execution. You should explicitly set the <A href="size-property-ado.md">Size</A> property for these parameters before calling the <A href="https://msdn.microsoft.com/en-us/library/jj248785(v=office.15)">Execute</A> method to prevent errors.</P>



**Fields**

Using the **Refresh** method on the **Fields** collection has no visible effect. To retrieve changes from the underlying database structure, you must use either the [Requery](requery-method-ado.md) method or, if the [Recordset](recordset-object-ado.md) object does not support bookmarks, the [MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) method.

**Properties**

Using the **Refresh** method on a **Properties** collection of some objects populates the collection with the dynamic properties that the provider exposes. These properties provide information about functionality specific to the provider, beyond the built-in properties ADO supports.

