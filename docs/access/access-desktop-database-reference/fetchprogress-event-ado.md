---
title: FetchProgress Event (ADO)
TOCTitle: FetchProgress Event (ADO)
ms:assetid: 09145d9a-ea5e-b41c-6c54-33ec83e642a9
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248828(v=office.15)
ms:contentKeyID: 48543114
ms.date: 09/18/2015
mtps_version: v=office.15
---

# FetchProgress Event (ADO)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameters  
Remarks  

The **FetchProgress** event is called periodically during a lengthy asynchronous operation to report how many more rows have currently been retrieved into the [Recordset](recordset-object-ado.md).

## Syntax

FetchProgress*Progress*, *MaxProgress*, *adStatus*, *pRecordset*

## Parameters

  - *Progress*

  - A **Long** value indicating the number of records that have currently been retrieved by the fetch operation.

  - *MaxProgress*

  - A **Long** value indicating the maximum number of records expected to be retrieved.

  - *adStatus*

  - An [EventStatusEnum](eventstatusenum.md) status value.

  - *pRecordset*

  - A **Recordset** object that is the object for which the records are being retrieved.

## Remarks

When using **FetchProgress** with a child **Recordset**, be aware that the *Progress* and *MaxProgress* parameter values are derived from the underlying [Cursor Service](microsoft-cursor-service-for-ole-db-ado-service-component.md) rowset. The values returned represent the total number of records in the underlying rowset, not just the number of records in the current chapter.


> [!NOTE]
> <P>To use <STRONG>FetchProgress</STRONG> with Microsoft Visual Basic, Visual Basic 6.0 or later is required.</P>


