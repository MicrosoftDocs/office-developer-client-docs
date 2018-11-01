﻿---
title: ADO objects and interfaces
TOCTitle: ADO objects and interfaces
ms:assetid: bebf4a80-8b6e-c43c-4138-897055cc60d3
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249927(v=office.15)
ms:contentKeyID: 48547471
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ADO objects and interfaces

**Applies to**: Access 2013, Office 2013

The relationships between these objects are represented in the ActiveX Data Objects (ADO) Object Model.

Each object can be contained in its corresponding collection. For example, an [Error](error-object-ado.md) object can be contained in an [Errors](errors-collection-ado.md) collection. For more information, see [ADO collections](ado-collections.md) or a specific collection topic.

<br/>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="even">
<th>Object</th>
<th>Description</th>
</tr>
<tr class="odd">
<td><p><a href="adorecordconstruction-interface-ado.md">ADORecordConstruction</a></p></td>
<td><p>Constructs an ADO <strong>Record</strong> object from an OLE DB <strong>Row</strong> object in a C/C++ application.</p></td>
</tr>
<tr class="even">
<td><p><a href="adorecordsetconstruction-interface-ado.md">ADORecordsetConstruction</a></p></td>
<td><p>Constructs an ADO <strong>Recordset</strong> object from an OLE DB <strong>Rowset</strong> object in a C/C++ application.</p></td>
</tr>
<tr class="odd">
<td><p><a href="error-object-ado.md">Command</a></p></td>
<td><p>Defines a specific command that you intend to execute against a data source.</p></td>
</tr>
<tr class="even">
<td><p><a href="field-object-ado.md">Connection</a></p></td>
<td><p>Represents an open connection to a data source.</p></td>
</tr>
<tr class="odd">
<td><p><a href="error-object-ado.md">Error</a></p></td>
<td><p>Contains details about data access errors that pertain to a single operation involving the provider.</p></td>
</tr>
<tr class="even">
<td><p><a href="field-object-ado.md">Field</a></p></td>
<td><p>Represents a column of data with a common data type.</p></td>
</tr>
<tr class="odd">
<td><p><a href="parameter-object-ado.md">Parameter</a></p></td>
<td><p>Represents a parameter or argument associated with a <strong>Command</strong> object based on a parameterized query or stored procedure.</p></td>
</tr>
<tr class="even">
<td><p><a href="property-object-ado.md">Property</a></p></td>
<td><p>Represents a dynamic characteristic of an ADO object that is defined by the provider.</p></td>
</tr>
<tr class="odd">
<td><p><a href="record-object-ado.md">Record</a></p></td>
<td><p>Represents a row of a <strong>Recordset</strong>, or a directory or file in a file system.</p></td>
</tr>
<tr class="even">
<td><p><a href="recordset-object-ado.md">Recordset</a></p></td>
<td><p>Represents the entire set of records from a base table or the results of an executed command. At any time, the <strong>Recordset</strong> object refers to only a single record within the set as the current record.</p></td>
</tr>
<tr class="odd">
<td><p><a href="stream-object-ado.md">Stream</a></p></td>
<td><p>Represents a binary stream of data.</p></td>
</tr>
</tbody>
</table>

<br/>

