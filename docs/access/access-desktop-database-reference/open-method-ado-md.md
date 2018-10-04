---
title: Open Method (ADO MD)
TOCTitle: Open Method (ADO MD)
ms:assetid: 12395ff6-fe07-325a-2b69-007aa0b11ee6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ248894(v=office.15)
ms:contentKeyID: 48543335
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Open Method (ADO MD)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameters  
Remarks  

Retrieves the results of a multidimensional query and returns the results to a cellset.

## Syntax

*Cellset*.Open*Source*, *ActiveConnection*

## Parameters

  - *Source*

  - Optional. A **Variant** that evaluates to a valid multidimensional query, such as a Multidimensional Expression (MDX) query. The *Source* argument corresponds to the [Source](source-property-ado-md.md) property. For more information about MDX, see the OLE DB for OLAP documentation in the Microsoft Data Access Components SDK.

  - *ActiveConnection*

  - Optional. A **Variant** that evaluates to a string specifying either a valid ADO [Connection](connection-object-ado.md) object variable name or a definition for a connection. The *ActiveConnection* argument specifies the connection in which to open the [Cellset](cellset-object-ado-md.md) object. If you pass a connection definition for this argument, ADO opens a new connection using the specified parameters. The *ActiveConnection* argument corresponds to the [ActiveConnection](activeconnection-property-ado-md.md) property.

## Remarks

The **Open** method generates an error if either of its parameters is omitted and its corresponding property value has not been set prior to attempting to open the **Cellset**.

