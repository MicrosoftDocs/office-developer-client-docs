---
title: TableDef members (DAO)
TOCTitle: TableDef Members
ms:assetid: bc55315e-bafe-d89e-ad31-fd4c9bb6486e
ms:mtpsurl: https://msdn.microsoft.com/library/Ff822714(v=office.15)
ms:contentKeyID: 48547408
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# TableDef members (DAO)


**Applies to**: Access 2013, Office 2013

A TableDef object represents the stored definition of a base table or a linked table (Microsoft Access workspaces only).

## Methods

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong><a href="tabledef-createfield-method-dao.md">CreateField</a></strong></p></td>
<td><p>Creates a new <strong><a href="field-object-dao.md">Field</a></strong> object (Microsoft Access workspaces only). .</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="tabledef-createindex-method-dao.md">CreateIndex</a></strong></p></td>
<td><p>Creates a new <strong><a href="index-object-dao.md">Index</a></strong> object (Microsoft Access workspaces only). .</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="tabledef-createproperty-method-dao.md">CreateProperty</a></strong></p></td>
<td><p>Creates a new user-defined <strong><a href="property-object-dao.md">Property</a></strong> object (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="tabledef-openrecordset-method-dao.md">OpenRecordset</a></strong></p></td>
<td><p>Creates a new <strong><a href="recordset-object-dao.md">Recordset</a></strong> object and appends it to the <strong>Recordsets</strong> collection.</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="tabledef-refreshlink-method-dao.md">RefreshLink</a></strong></p></td>
<td><p>Updates the connection information for a linked table (Microsoft Access workspaces only).</p></td>
</tr>
</tbody>
</table>


## Properties

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong><a href="tabledef-attributes-property-dao.md">Attributes</a></strong></p></td>
<td><p>Sets or returns a value that indicates one or more characteristics of a <strong>TableDef</strong> object. Read/write <strong>Long</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="tabledef-conflicttable-property-dao.md">ConflictTable</a></strong></p></td>
<td><p>Returns the name of a conflict table containing the database records that conflicted during the synchronization of two replicas (Microsoft Access workspaces only). Read-only <strong>String</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="tabledef-connect-property-dao.md">Connect</a></strong></p></td>
<td><p>Sets or returns a value that provides information about a linked table. Read/write <strong>String</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="tabledef-datecreated-property-dao.md">DateCreated</a></strong></p></td>
<td><p>Returns the date and time that an object was created (Microsoft Access workspaces only). Read-only <strong>Variant</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="tabledef-fields-property-dao.md">Fields</a></strong></p></td>
<td><p>Returns a <strong>Fields</strong> collection that represents all stored <strong>Field</strong> objects for the specified object. Read-only.</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="tabledef-indexes-property-dao.md">Indexes</a></strong></p></td>
<td><p>Returns an <strong>Indexes</strong> collection that contains all of the stored <strong>Index</strong> objects for the specified table. Read-only.</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="tabledef-lastupdated-property-dao.md">LastUpdated</a></strong></p></td>
<td><p>Returns the date and time of the most recent change made to an object. Read-only <strong>Variant</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="tabledef-name-property-dao.md">Name</a></strong></p></td>
<td><p>Returns or sets the name of the specified object. Read/write <strong>String</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="tabledef-properties-property-dao.md">Properties</a></strong></p></td>
<td><p>Returns the <strong><a href="properties-collection-dao.md">Properties</a></strong> collection of the specified object. Read-only.</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="tabledef-recordcount-property-dao.md">RecordCount</a></strong></p></td>
<td><p>Returns the total number of records in a <strong><a href="tabledef-object-dao.md">TableDef</a></strong> object. Read-only <strong>Long</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="tabledef-replicafilter-property-dao.md">ReplicaFilter</a></strong></p></td>
<td><p>Sets or returns a value on a <strong><a href="tabledef-object-dao.md">TableDef</a></strong> object within a partial replica that indicates which subset of records is replicated to that table from a full replica. (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="tabledef-sourcetablename-property-dao.md">SourceTableName</a></strong></p></td>
<td><p>Sets or returns a value that specifies the name of a linked table or the name of a base table (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="tabledef-updatable-property-dao.md">Updatable</a></strong></p></td>
<td><p>Returns a value that indicates whether you can change a DAO object. Read-only <strong>Boolean</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="tabledef-validationrule-property-dao.md">ValidationRule</a></strong></p></td>
<td><p>Sets or returns a value that validates the data in a field as it's changed or added to a table (Microsoft Access workspaces only).Read/write <strong>String</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="tabledef-validationtext-property-dao.md">ValidationText</a></strong></p></td>
<td><p>Sets or returns a value that specifies the text of the message that your application displays if the value of a <strong>Field</strong> object doesn't satisfy the validation rule specified by the <strong>ValidationRule</strong> property setting (Microsoft Access workspaces only). Read/write <strong>String</strong>.</p></td>
</tr>
</tbody>
</table>

