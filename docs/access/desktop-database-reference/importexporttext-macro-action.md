---
title: ImportExportText macro action
TOCTitle: ImportExportText macro action
ms:assetid: 366fa095-6f09-7c22-e734-bfa585cfe79e
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192475(v=office.15)
ms:contentKeyID: 48544171
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm168097
f1_categories:
- Office.Version=v15
localization_priority: Normal
---

# ImportExportText macro action

**Applies to**: Access 2013, Office 2013

You can use the **ImportExportText** action to import or export text between the current Microsoft Access database (.mdb or .accdb) or Access project (.adp) and a text file. You can also link the data in a text file to the current Access database. With a linked text file, you can view the text data with Access while still allowing complete access to the data from your word processing program. You can also import from, export to, and link to a table or list in an HTML file (\*.html).

> [!NOTE]
> If you link to data in a text file or an HTML file, the data is read-only in Access. This action will not be allowed if the database is not trusted. 

## Setting

The **ImportExportText** action has the following arguments.

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
<td><p><strong>Transfer Type</strong></p></td>
<td><p>The type of transfer you want to make. You can import data from, export data to, or link to data in delimited or fixed-width text files or HTML files. You can also export data to a Microsoft Word mail merge data file, which you can then use with the Word mail merge feature to create merged documents such as form letters and mailing labels. Select <strong>Import Delimited</strong>, <strong>Import Fixed Width</strong>, <strong>Import HTML</strong>, <strong>Export Delimited</strong>, <strong>Export Fixed Width</strong>, <strong>Export HTML</strong>, <strong>Export Word for Windows Merge</strong>, <strong>Link Delimited</strong>, <strong>Link Fixed Width</strong>, or <strong>Link HTML</strong> in the <strong>Transfer Type</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. The default is <strong>Import Delimited</strong>.</p><p><strong>NOTE</strong>: Only <STRONG>Import Delimited</STRONG>, <STRONG>Import Fixed Width</STRONG>, <STRONG>Export Delimited</STRONG>, <STRONG>Export Fixed Width</STRONG>, or <STRONG>Export Word for Windows Merge</STRONG> transfer types are supported in an Access project (.adp).</p></td>
</tr>
<tr class="even">
<td><p><strong>Specification Name</strong></p></td>
<td><p>The specification name for the set of options that determines how a text file is imported or linked. For a fixed-width text file, you must either specify an argument or use a schema.ini file, which must be stored in the same folder as the imported or linked text file.</p>
<p>To create a specification for importing or linking a text file:</p>
<ol>
<li><p>In the <strong>Get External Data</strong> dialog box, enter the path of the source text file in the <strong>File name</strong> box.</p></li>
<li><p>Click the option you want for storing the data (import, append, or link), and click <strong>OK</strong>.</p></li>
<li><p>In the <strong>Import Text Wizard</strong> dialog box, click <strong>Advanced</strong>.</p></li>
<li><p>Specify the options you want for this specification, then click <strong>Save As</strong>.</p></li>
<li><p>Enter the name you want for the specification, then click <strong>OK</strong>.</p></li>
<li><p>You can manage existing specifications by clicking <strong>Specs</strong> in the specification dialog box.</p></li>
<li><p>Click <strong>OK</strong> to close the specification dialog box.</p></li>
</ol>
<p></p>
<p>You can then type the specification name in this argument whenever you want to import or export the same type of text file. You can import, export, or link delimited text files without typing a specification name for this argument. In this case, Access uses the defaults from the wizard dialog box. Access uses a predetermined format for mail merge data files, so you don't ever need to type a specification name for this argument when you export these types of files. You can use import/export specifications with HTML files, but the only part of the specification that applies is the specification for data type formatting.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Table Name</strong></p></td>
<td><p>The name of the Access table to import text data to, export text data from, or link text data to. You can also type the name of the Access query you want to export data from. This is a required argument. If you click <strong>Import Delimited</strong>, <strong>Import Fixed Width</strong>, or <strong>Import HTML</strong> in the <strong>Transfer Type</strong> box, Access appends the text data to this table if the table already exists. Otherwise, Access creates a new table containing the text data. You can't use an SQL statement to specify data to export when you are using the <strong>ImportExportText</strong> action. Instead of using an SQL statement, you must first create a query and then specify the name of the query in the <strong>Table Name</strong> argument.</p></td>
</tr>
<tr class="even">
<td><p><strong>File Name</strong></p></td>
<td><p>The name of the text file to import from, export to, or link to. Include the full path. This is a required argument. Access creates a new text file when you export data from Access. If the file name is the same as the name of an existing text file, Access replaces the existing text file. If you want to import or link a particular table or list in an HTML file, you can use the <strong>HTML Table Name</strong> argument.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Has Field Names</strong></p></td>
<td><p>Specifies whether the first row of the text file contains the names of the fields. If you select <strong>Yes</strong>, Access uses the names in this row as field names in the Access table when you import or link the text data. If you select <strong>No</strong>, Access treats the first row as a normal row of data. The default is <strong>No</strong>.<br/><br/>Access ignores this argument for Word for Windows mail merge data files because the first row must contain the field names. When you export an Access table or select query to a delimited or fixed-width text file, Access inserts the field names of your table or select query into the first row of the text file if you've selected <strong>Yes</strong> for this argument.<br/><br/>If you are importing or linking a fixed-width text file and select <strong>Yes</strong> in this box, the first row containing the field names must use the field delimiter set in the import/export specification to separate the field names. If you are exporting to a fixed-width text file and select <strong>Yes</strong> for this argument, Access inserts the field names into the first row of the text file with this delimiter.</p></td>
</tr>
<tr class="even">
<td><p><strong>HTML Table Name</strong></p></td>
<td><p>The name of the table or list in the HTML file that you want to import or link. This argument is ignored unless the <strong>Transfer Type</strong> argument is set to Import HTML or Link HTML. If you leave this argument blank, the first table or list in the HTML file is imported or linked. <br/><br/>The table or list name in the HTML file is determined by the text specified by the &lt;CAPTION&gt; tag, if there's a &lt;CAPTION&gt; tag. If there's no &lt;CAPTION&gt; tag, the name is determined by the text specified by the &lt;TITLE&gt; tag. If more than one table or list has the same name, Access distinguishes them by adding a number to the end of each name; for example, Employees1 and Employees2.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Code Page</strong></p></td>
<td><p>The name of the character set used with the code page.</p></td>
</tr>
</tbody>
</table>


## Remarks

You can export the data in Access select queries to text files. Access exports the result set of the query, treating it just like a table.

Text data that you append to an existing Access table must be compatible with the table's structure.

- Each field in the text must be of the same data type as the corresponding field in the table.

- The fields must be in the same order (unless you set the **Has Field Names** argument to **Yes**, in which case the field names in the text must match the field names in the table).

This action is similar to clicking **Text File** in the **Import** or **Export** group on the **External Data** tab. The arguments of the **ImportExportText** action reflect the options in the wizard started by the **Text File** command.

> [!TIP]
> An import/export specification stores the information Access needs to import, export, or link a text file. You can use stored specifications to import, export, or link text data from or to similar text files. For example, you might receive weekly sales figures in a text file from a mainframe computer. You can create and save a specification for this type of data and then use the specification whenever you add this data to your Access database.

> [!NOTE]
> If you query or filter a linked text file, the query or filter is case-sensitive.

To run the **ImportExportText** action in a Visual Basic for Applications (VBA) module, use the **TransferText** method of the **DoCmd** object.

