---
title: ImportExportData macro action
TOCTitle: ImportExportData macro action
ms:assetid: 2cbde873-8a3d-b15c-4aab-405cddf44cea
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192107(v=office.15)
ms:contentKeyID: 48543961
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm51789
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# ImportExportData macro action

**Applies to**: Access 2013, Office 2013

You can use the **ImportExportData** action to import or export data between the current Access database (.mdb or .accdb) or Access project (.adp) and another database. For Microsoft Access databases, you can also link a table to the current Access database from another database. With a linked table, you have access to the table's data while the table itself remains in the other database.

> [!NOTE]
> This action will not be allowed if the database is not trusted. 

## Settings

The **ImportExportData** action has the following arguments.

<table>
<colgroup>
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Action argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Transfer Type</strong></p></td>
<td><p>The type of transfer you want to make. Select <strong>Import</strong>, <strong>Export</strong>, or <strong>Link</strong> in the <strong>Transfer Type</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. The default is <strong>Import</strong>.</p><p><strong>NOTE</strong>: The <strong>Link</strong> transfer type is not supported for Access projects (.adp).</p></td>
</tr>
<tr class="even">
<td><p><strong>Database Type</strong></p></td>
<td><p>The type of database to import from, export to, or link to. You can select <strong>Microsoft Access</strong> or one of a number of other database types in the <strong>Database Type</strong> box. The default is <strong>Microsoft Access</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Database Name</strong></p></td>
<td><p>The name of the database to import from, export to, or link to. Include the full path. This is a required argument. For types of databases that use separate files for each table, such as FoxPro, Paradox, and dBASE, enter the directory containing the file. Enter the file name in the <strong>Source</strong> argument (to import or link) or the <strong>Destination</strong> argument (to export). For ODBC databases, type the full Open Database Connectivity (ODBC) connection string.</p>
<p>To see an example of a connection string, link an external table to Access:</p>
<ol>
<li><p>In the <strong>Get External Data</strong> dialog box, enter the path of your source database in the <strong>File name</strong> box.</p></li>
<li><p>Click <strong>Link to the data source by creating a linked table</strong>, and click <strong>OK</strong>.</p></li>
<li><p>Select a table in the <strong>Link Tables</strong> dialog box, and click <strong>OK</strong>.</p></li>
</ol>
<p>Open the newly linked table in Design view and view the table properties by clicking <strong>Property Sheet</strong> on the <strong>Design</strong> tab, under <strong>Tools</strong>. The text in the <strong>Description</strong> property setting is the connection string for this table.</p>
<p>For more information about ODBC connection strings, see the Help file or other documentation for the ODBC driver of this type of ODBC database.</p></td>
</tr>
<tr class="even">
<td><p><strong>Object Type</strong></p></td>
<td><p>The type of object to import or export. If you select <strong>Microsoft Access</strong> for the <strong>Database Type</strong> argument, you can select <strong>Table</strong>, <strong>Query</strong>, <strong>Form</strong>, <strong>Report</strong>, <strong>Macro</strong>, <strong>Module</strong>, <strong>Data Access Page</strong>, <strong>Server View</strong>, <strong>Diagram</strong>, <strong>Stored Procedure</strong>, or <strong>Function</strong> in the <strong>Object Type</strong> box. The default is <strong>Table</strong>. If you select any other type of database, or if you select <strong>Link</strong> in the <strong>Transfer Type</strong> box, this argument is ignored. If you are exporting a select query to an Access database, select <strong>Table</strong> in this argument to export the result set of the query, and select <strong>Query</strong> to export the query itself. If you are exporting a select query to another type of database, this argument is ignored and the result set of the query is exported.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Source</strong></p></td>
<td><p>The name of the table, select query, or Access object that you want to import, export, or link. For some types of databases, such as FoxPro, Paradox, or dBASE, this is a file name. Include the file name extension (such as .dbf) in the file name. This is a required argument.</p></td>
</tr>
<tr class="even">
<td><p><strong>Destination</strong></p></td>
<td><p>The name of the imported, exported, or linked table, select query, or Access object in the destination database. For some types of databases, such as FoxPro, Paradox, or dBASE, this is a file name. Include the file name extension (such as .dbf) in the file name. This is a required argument. If you select <strong>Import</strong> in the <strong>Transfer Type</strong> argument and <strong>Table</strong> in the <strong>Object Type</strong> argument, Access creates a new table containing the data in the imported table. If you import a table or other object, Access adds a number to the name if it conflicts with an existing name. For example, if you import Employees and Employees already exists, Access renames the imported table or other object Employees1. If you export to an Access database or another database, Access automatically replaces any existing table or other object that has the same name.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Structure Only</strong></p></td>
<td><p>Specifies whether to import or export only the structure of a database table without any of its data. Select <strong>Yes</strong> or <strong>No</strong>. The default is <strong>No</strong>.</p></td>
</tr>
</tbody>
</table>


## Remarks

You can import and export tables between Access and other types of databases. You can also export Access select queries to other types of databases. Access exports the result set of the query in the form of a table. You can import and export any Access database object if both databases are Access databases.

If you import a table from another Access database (.mdb or .accdb) that's a linked table in that database, it will still be linked after you import it. That is, the link is imported, not the table itself.

If the database you're accessing requires a password, a dialog box appears when you run the macro. Type the password in this dialog box.

The **ImportExportData** action is similar to the commands on the **External Data** tab, under **Import** or **Export**. You can use these commands to select a source of data, such as an Access database or another type of database, a spreadsheet, or a text file. If you select a database, one or more dialog boxes appear in which you select the type of object to import or export (for Access databases), the name of the object, and other options, depending on the database you are importing from or exporting or linking to. The arguments for the **ImportExportData** action reflect the options in these dialog boxes.

If you want to supply index information for a linked dBASE table, first link the table:

1.  Click **dBASE File**.

2.  In the **Get External Data** dialog box, enter the path for the dBASE file in the **File name** box.

3.  Click **Link to the data source by creating a linked table**, then click **OK**.

4.  Specify the indexes in the dialog boxes for this command. Access stores the index information in a special information (.inf) file, located in the Microsoft Office folder.

5.  You can then delete the link to the linked table.

The next time you use the **ImportExportData** action to link this dBASE table, Access uses the index information that you've specified.

> [!NOTE]
> If you query or filter a linked table, the query or filter is case-sensitive.

To run the **ImportExportData** action in a Visual Basic for Applications (VBA) module, use the **TransferDatabase** method of the **DoCmd** object.

