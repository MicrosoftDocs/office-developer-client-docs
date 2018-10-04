---
title: Index Members (DAO)
TOCTitle: Index Members
ms:assetid: e261c5fa-ca7d-0d63-1c29-48e9231b39d1
ms:mtpsurl: https://msdn.microsoft.com/library/Ff835712(v=office.15)
ms:contentKeyID: 48548290
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Index Members (DAO)


**Applies to**: Access 2013 | Office 2013

Index objects specify the order of records accessed from database tables and whether or not duplicate records are accepted, providing efficient access to data. For external databases, Index objects describe the indexes established for external tables (Microsoft Access workspaces only).

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
<td><p><strong><a href="index-createfield-method-dao.md">CreateField</a></strong></p></td>
<td><p>Creates a new <strong><a href="field-object-dao.md">Field</a></strong> object (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="index-createproperty-method-dao.md">CreateProperty</a></strong></p></td>
<td><p>Creates a new user-defined <strong><a href="property-object-dao.md">Property</a></strong> object (Microsoft Access workspaces only).</p></td>
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
<td><p><strong><a href="index-clustered-property-dao.md">Clustered</a></strong></p></td>
<td><p>Sets or returns a value that indicates whether an <strong>Index</strong> object represents a clustered index for a table (Microsoft Access workspaces only). Read/write <strong>Boolean</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="index-distinctcount-property-dao.md">DistinctCount</a></strong></p></td>
<td><p>Returns a value that indicates the number of unique values for the <strong><a href="index-object-dao.md">Index</a></strong> object that are included in the associated table (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="index-fields-property-dao.md">Fields</a></strong></p></td>
<td><p>Returns a <strong>Fields</strong> collection that represents all stored <strong>Field</strong> objects for the specified object. Read/write.</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="index-foreign-property-dao.md">Foreign</a></strong></p></td>
<td><p>Returns a value that indicates whether an <strong><a href="index-object-dao.md">Index</a></strong> object represents a foreign key in a table (Microsoft Access workspaces only). .</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="index-ignorenulls-property-dao.md">IgnoreNulls</a></strong></p></td>
<td><p>Sets or returns a value that indicates whether records that have Null values in their index fields have index entries (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="index-name-property-dao.md">Name</a></strong></p></td>
<td><p>Returns or sets the name of the specified object. Read/write <strong>String</strong> if the object has not been appended to a collection. Read-only <strong>String</strong> if the object has been appended to a collection.</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="index-primary-property-dao.md">Primary</a></strong></p></td>
<td><p>Sets or returns a value that indicates whether an <strong><a href="index-object-dao.md">Index</a></strong> object represents a primary key index for a table (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="index-properties-property-dao.md">Properties</a></strong></p></td>
<td><p>Returns the <strong><a href="properties-collection-dao.md">Properties</a></strong> collection of the specified object. Read-only.</p></td>
</tr>
<tr class="odd">
<td><p><strong><a href="index-required-property-dao.md">Required</a></strong></p></td>
<td><p>Sets or returns a value that indicates whether a <strong><a href="field-object-dao.md">Field</a></strong> object requires a non-Null value.</p></td>
</tr>
<tr class="even">
<td><p><strong><a href="index-unique-property-dao.md">Unique</a></strong></p></td>
<td><p>Sets or returns a value that indicates whether an <strong><a href="index-object-dao.md">Index</a></strong> object represents a unique (key) index for a table (Microsoft Access workspaces only).</p></td>
</tr>
</tbody>
</table>

