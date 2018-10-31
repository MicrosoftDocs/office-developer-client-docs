---
title: CopyDatabaseFile Macro Action
TOCTitle: CopyDatabaseFile Macro Action
ms:assetid: e6320b55-946b-9efc-9b64-b86513801a37
ms:mtpsurl: https://msdn.microsoft.com/library/Ff835963(v=office.15)
ms:contentKeyID: 48548373
ms.date: 09/18/2015
mtps_version: v=office.15
---

# CopyDatabaseFile Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **CopyDatabaseFile** action to make a copy of the current Microsoft SQL Server 7.0 or later database connected to your Access project. Access detaches the current database and then attaches it to the destination server. For more information about detaching and attaching a database, see the SQL Server documentation.


> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the See Also section of this article.



## Setting

The **CopyDatabaseFile** action has the following arguments.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Action argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Database File Name</strong></p></td>
<td><p>The name of the new Master Data File. The default path for the file is the current location of the Access project file (.adp).</p></td>
</tr>
<tr class="even">
<td><p><strong>Overwrite Existing File</strong></p></td>
<td><p>Specifies whether or not to replace an existing file with the same name. If set to <strong>Yes</strong> and the filename already exists, the file is overwritten. If set to <strong>No</strong> and the filename already exists, the file is not overwritten and the action fails. If the file does not already exist, this setting is ignored. The default is <strong>Yes</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Disconnect All Users</strong></p></td>
<td><p>Specifies whether or not Access should force users off the database. If set to <strong>Yes</strong>, any users that are connected to the current database are disconnected so that the copy database operation can proceed. If set to <strong>No</strong> and one or more users are connected to the database, the copy database operation fails. The default is <strong>No</strong>.</p>

> [!WARNING]
> Disconnecting users from a database without adequate warning can lead to data loss.


<p></p></td>
</tr>
</tbody>
</table>


## Remarks

The copy operation is synchronous, so you can't perform other operations until the copy of the database is complete.

The **CopyDatabaseFile** action not only copies data, data definitions, and database objects, but also copies extended properties, such as default values, text constraints, and lookup values.

Requirements for copying a database:

  - You must disconnect all applications and users before you copy the database file.

  - All objects and views except the Navigation Pane must be closed.

  - The current database must not be replicated.

  - The source server database must be Microsoft SQL Server version 7.0 or later, or SQL Server 2000 Desktop Engine running on a local computer.

<!-- end list -->

  - The SQL Server database on the source server must be a single file database.

  - You must be a member of the sysadmin role on both the source and destination SQL Server computers.

To run the **CopyDatabaseFile** action in a Visual Basic for Applications module, use the **CopyDatabaseFile** method of the **DoCmd** object.

