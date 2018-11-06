---
title: TransferSQLDatabase macro action
TOCTitle: TransferSQLDatabase macro action
ms:assetid: 8cb95e22-f1f0-6c70-7dcb-3a3e9aafdc57
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197344(v=office.15)
ms:contentKeyID: 48546244
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm111536
f1_categories:
- Office.Version=v15
---

# TransferSQLDatabase macro action

**Applies to**: Access 2013, Office 2013

In an Access project, you can use the **TransferSQLDatabase** action to transfer a Microsoft SQL Server 7.0 or later database to another SQL Server 7.0 or later database. For more information about transferring a database, see the SQL Server documentation.

> [!NOTE]
> This action will not be allowed if the database is not trusted.

## Setting

The **TransferSQLDatabase** action has the following arguments.

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
<td><p><strong>Server</strong></p></td>
<td><p>The name of the SQL Server 7.0 or later database server you are copying to.</p></td>
</tr>
<tr class="even">
<td><p><strong>Database</strong></p></td>
<td><p>The name of the new database that will be created on the destination server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Use Trusted Connection</strong></p></td>
<td><p>Specifes whether or not there is a trusted connection to the SQL Server. If set to <strong>Yes</strong>, then there is a trusted connection and the <strong>Login</strong> and <strong>Password</strong> arguments are not required. If set to <strong>No</strong>, the <strong>Login</strong> and <strong>Password</strong> arguments are required. The default is <strong>Yes</strong>. When you use a trusted connection, SQL Server security integrates with the Windows operating system security to provide a single log on to the network and the database.</p></td>
</tr>
<tr class="even">
<td><p><strong>Login</strong></p></td>
<td><p>The name of the Login to the destination server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Password</strong></p></td>
<td><p>The password for the <strong>Login</strong> argument. This password is stored as text in the Access project, but is hidden during the transfer database operation.</p></td>
</tr>
<tr class="even">
<td><p><strong>Transfer Copy Data</strong></p></td>
<td><p>Specifies whether or not to include data in the transfer database operation. When set to <strong>Yes</strong>, all data is included for all the tables, along with all data structures, extended properties, and database objects. When set to <strong>No</strong>, no data is included from the tables. Only the table structure and extended properties are created on the destination server, along with all other database objects (except database diagrams). The default is <strong>Yes</strong>.</p></td>
</tr>
</tbody>
</table>


## Remarks

You cannot perform other operations while the database is being transferred.

The **TransferSQLDatabase** action, by default, copies data, data definitions, database objects, and extended properties, such as default values, text constraints, and lookup values.

There are requirements for transferring a database:

- You must be a member of the sysadmin role on the destination server (No special role is required on the source server).

- The current SQL server connected to the Access project and the destination server you are transferring the database to must be SQL Server version 7.0 or later.

  > [!NOTE]
  > Linked servers are not transferred during a database transfer operation.

To run the **TransferSQLDatabase** action in a Visual Basic for Applications (VBA) module, use the **TransferSQLDatabase** method of the **DoCmd** object.

