---
title: Connection.CreateQueryDef Method (DAO)
TOCTitle: CreateQueryDef Method
ms:assetid: 254fe81a-9b45-e8e7-108d-503c1c1c0fcc
ms:mtpsurl: https://msdn.microsoft.com/library/Ff191860(v=office.15)
ms:contentKeyID: 48543781
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1053067
f1_categories:
- Office.Version=v15
---

# Connection.CreateQueryDef Method (DAO)


**Applies to**: Access 2013, Office 2013

Creates a new **[QueryDef](querydef-object-dao.md)** object.

## Syntax

*expression* .CreateQueryDef(***Name***, ***SQLText***)

*expression* A variable that represents a **Connection** object.

### Parameters

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Required/Optional</p></th>
<th><p>Data Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>A <strong>Variant</strong> (<strong>String</strong> subtype) that uniquely names the new <strong>QueryDef</strong>.</p></td>
</tr>
<tr class="even">
<td><p>SQLText</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>A <strong>Variant</strong> (<strong>String</strong> subtype) that is an SQL statement defining the <strong>QueryDef</strong>. If you omit this argument, you can define the <strong>QueryDef</strong> by setting its <strong><a href="querydef-sql-property-dao.md">SQL</a></strong> property before or after you append it to a collection.</p></td>
</tr>
</tbody>
</table>


### Return Value

QueryDef

## Remarks

In a Microsoft Access workspace, if you provide anything other than a zero-length string for the name when you create a **QueryDef**, the resulting **QueryDef** object is automatically appended to the **[QueryDefs](querydefs-collection-dao.md)** collection.

If the object specified by name is already a member of the **QueryDefs** collection, a run-time error occurs. You can create a temporary **QueryDef** by using a zero-length string for the name argument when you execute the **CreateQueryDef** method. You can also accomplish this by setting the **[Name](connection-name-property-dao.md)** property of a newly created **QueryDef** to a zero-length string (""). Temporary **QueryDef** objects are useful if you want to repeatedly use dynamic SQL statements without having to create any new permanent objects in the **QueryDefs** collection. You can't append a temporary **QueryDef** to any collection because a zero-length string isn't a valid name for a permanent **QueryDef** object. You can always set the **Name** and **SQL** properties of the newly created **QueryDef** object and subsequently append the **QueryDef** to the **QueryDefs** collection.

To run the SQL statement in a **QueryDef** object, use the **[Execute](connection-execute-method-dao.md)** or **[OpenRecordset](connection-openrecordset-method-dao.md)** method.

Using a **QueryDef** object is the preferred way to perform SQL pass-through queries with ODBC databases.

To remove a **QueryDef** object from a **QueryDefs** collection in a Microsoft Access database engine database, use the **[Delete](fields-delete-method-dao.md)** method on the collection.

