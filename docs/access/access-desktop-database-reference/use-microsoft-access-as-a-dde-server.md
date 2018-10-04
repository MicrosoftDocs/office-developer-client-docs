---
title: Use Microsoft Access as a DDE Server
TOCTitle: Use Microsoft Access as a DDE Server
ms:assetid: a3e82bf7-94b5-8eec-86bc-2d5387d66738
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff821067(v=office.15)
ms:contentKeyID: 48546801
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm5186349
f1_categories:
- Office.Version=v15
---

# Use Microsoft Access as a DDE Server


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
The System Topic  
The  
The TABLE  

Microsoft Access supports dynamic data exchange (DDE) as either a destination (client) application or a source (server) application. For example, an application such as Microsoft Word, acting as a client, can request data through DDE from a Microsoft Access database that's acting as a server.


> [!TIP]
> <P>If you need to manipulate Microsoft Access objects from another application, you may want to consider using Automation.</P>



A DDE conversation between a client and server is established on a particular topic. A topic can be either a data file in the format supported by the server application, or it can be the System topic, which supplies information about the server application itself. Once a conversation has begun on a particular topic, only a data item associated with that topic can be transferred.

For example, suppose you are running Microsoft Word and want to insert data from a particular Microsoft Access database into a document. You begin a DDE conversation with Microsoft Access by opening a DDE channel with the **DDEInitiate** function and specifying the database file name as the topic. You can then transfer data from that database to Microsoft Word through that channel.

As a DDE server, Microsoft Access supports the following topics:

  - The System topic

  - The name of a database (*database* topic)

  - The name of a table (*tablename* topic)

  - The name of a query (*queryname* topic)

  - A Microsoft Access SQL string (*sqlstring* topic)

Once you've established a DDE conversation, you can use the **DDEExecute** statement to send a command from the client to the server application. When used as a DDE server, Microsoft Access recognizes any of the following as a valid command:

  - The name of a macro in the current database.

  - Any action that you can carry out in Visual Basic by using one of the methods of the **DoCmd** object.

  - The OpenDatabase and CloseDatabase actions, which are used only for DDE operations. (For an example of how to use these actions, see the example later in this topic.)


> [!NOTE]
> <P>When you specify a macro action as a <STRONG>DDEExecute</STRONG> statement, the action and any arguments follow the <STRONG>DoCmd</STRONG> object syntax and must be enclosed in brackets ([ ]). However, applications that support DDE don't recognize intrinsic constants in DDE operations. Also, string arguments must be enclosed in quotation marks (" ") if the string contains a comma. Otherwise, quotation marks aren't required.</P>



The client application can use the **DDERequest** function to request text data from the server application over an open DDE channel. Or the client can use the **DDEPoke** statement to send data to the server application. Once the data transfer is complete, the client can use the **DDETerminate** statement to close the DDE channel, or the **DDETerminateAll** statement to close all open channels.


> [!NOTE]
> <P>When your client application has finished receiving data over a DDE channel, it should close that channel to conserve memory resources.</P>



The following example demonstrates how to create a Microsoft Word procedure with Visual Basic that uses Microsoft Access as a DDE server. (For this example to work, Microsoft Access must be running.)

    Sub AccessDDE() 
        Dim intChan1 As Integer, intChan2 As Integer 
        Dim strQueryData As String 
     
        ' Use System topic to open Northwind sample database. 
        ' Database must be open before using other DDE topics. 
        intChan1 = DDEInitiate("MSAccess", "System") 
        ' You may need to change this path to point to actual location 
        ' of Northwind sample database. 
        DDEExecute intChan1, "[OpenDatabase C:\Access\Samples\Northwind.mdb]" 
     
        ' Get all data from Ten Most Expensive Products query. 
        intChan2 = DDEInitiate("MSAccess", "Northwind.mdb;" _ 
            & "QUERY Ten Most Expensive Products") 
        strQueryData = DDERequest(intChan2, "All") 
        DDETerminate intChan2 
     
        ' Close database. 
        DDEExecute intChan1, "[CloseDatabase]" 
        DDETerminate intChan1 
     
        ' Print retrieved data to Debug Window. 
        Debug.Print strQueryData 
    End Sub

The following sections provide information about the valid DDE topics supported by Microsoft Access.

## The System Topic

The System topic is a standard topic for all Microsoft Windows–based applications. It supplies information about the other topics supported by the application. To access this information, your code must first call the **DDEInitiate** function with as the *topic* argument, and then execute the **DDERequest** statement with one of the following supplied for the *item* argument.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Item</p></th>
<th><p>Returns</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SysItems</p></td>
<td><p>A list of items supported by the System topic in Microsoft Access.</p></td>
</tr>
<tr class="even">
<td><p>Formats</p></td>
<td><p>A list of the formats Microsoft Access can copy onto the Clipboard.</p></td>
</tr>
<tr class="odd">
<td><p>Status</p></td>
<td><p>&quot;Busy&quot; or &quot;Ready&quot;.</p></td>
</tr>
<tr class="even">
<td><p>Topics</p></td>
<td><p>A list of all open databases.</p></td>
</tr>
</tbody>
</table>


The following example demonstrates the use of the **DDEInitiate** and **DDERequest** functions with the System topic:

    ' In Visual Basic, initiate DDE conversation with Microsoft Access. 
    Dim intChan1 As Integer, strResults As String 
    intChan1 = DDEInitiate("MSAccess", "System") 
    ' Request list of topics supported by System topic. 
    strResults = DDERequest(intChan1, "SysItems") 
    ' Run OpenDatabase action to open Northwind.mdb. 
    ' You may need to change this path to point to actual location 
    ' of Northwind sample database. 
    DDEExecute intChan1, "[OpenDatabase C:\Access\Samples\Northwind.mdb]"

## The

The *database* topic is the file name of an existing database. You can type either just the base name (Northwind), or its path and .mdb extension (C:\\Access\\Samples\\Northwind.mdb). After you start a DDE conversation with the database, you can request a list of the objects in that database.


> [!NOTE]
> <P>You can't use DDE to query the Microsoft Access workgroup information file.</P>



The *database* topic supports the following items.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Item</p></th>
<th><p>Returns</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TableList</p></td>
<td><p>A list of tables.</p></td>
</tr>
<tr class="even">
<td><p>QueryList</p></td>
<td><p>A list of queries.</p></td>
</tr>
<tr class="odd">
<td><p>FormList</p></td>
<td><p>A list of forms.</p></td>
</tr>
<tr class="even">
<td><p>ReportList</p></td>
<td><p>A list of reports.</p></td>
</tr>
<tr class="odd">
<td><p>MacroList</p></td>
<td><p>A list of macros.</p></td>
</tr>
<tr class="even">
<td><p>ModuleList</p></td>
<td><p>A list of modules.</p></td>
</tr>
<tr class="odd">
<td><p>ViewList</p></td>
<td><p>A list of views</p></td>
</tr>
<tr class="even">
<td><p>StoredProcedureList</p></td>
<td><p>A list of stored procedures</p></td>
</tr>
<tr class="odd">
<td><p>DatabaseDiagramList</p></td>
<td><p>A list of database diagrams</p></td>
</tr>
</tbody>
</table>


The following example shows how you can open the Employees form in the Northwind sample database from a Visual Basic procedure:

    ' In Visual Basic, initiate DDE conversation with 
    ' Northwind sample database. 
    ' Make sure database is open. 
    intChan2 = DDEInitiate("MSAccess", "Northwind") 
    ' Request list of forms in Northwind sample database. 
    strResponse = DDERequest(intChan2, "FormList") 
    ' Run OpenForm action and arguments to open Employees form. 
    DDEExecute intChan2, "[OpenForm Employees,0,,,1,0]"

## The TABLE

These topics use the following syntax:

*databasename***; TABLE***tablename*

*databasename***; QUERY***queryname*

*databasename***; SQL \[***sqlstring***\]**

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Part</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>databasename</em></p></td>
<td><p>The name of the database that the table or query is in or that the SQL statement applies to, followed by a semicolon (;). The database name can be just the base name (Northwind) or its full path and .mdb extension (C:\Access\Samples\Northwind.mdb).</p></td>
</tr>
<tr class="even">
<td><p><em>tablename</em></p></td>
<td><p>The name of an existing table.</p></td>
</tr>
<tr class="odd">
<td><p><em>queryname</em></p></td>
<td><p>The name of an existing query.</p></td>
</tr>
<tr class="even">
<td><p><em>sqlstring</em></p></td>
<td><p>A valid SQL statement up to 256 characters long, ending with a semicolon. To exchange more than 256 characters, omit this argument and instead use successive <strong>DDEPoke</strong> statements to build an SQL statement. For example, the following Visual Basic code uses the <strong>DDEPoke</strong> statement to build an SQL statement and then request the results of the query.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


The following table lists the valid items for the TABLE *tablename*, QUERY *queryname*, and SQL *sqlstring* topics.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Item</p></th>
<th><p>Returns</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>All</p></td>
<td><p>All the data in the table, including field names.</p></td>
</tr>
<tr class="even">
<td><p>Data</p></td>
<td><p>All rows of data, without field names.</p></td>
</tr>
<tr class="odd">
<td><p>FieldNames</p></td>
<td><p>A single-row list of field names.</p></td>
</tr>
<tr class="even">
<td><p>FieldNames;T</p></td>
<td><p>A two-row list of field names (first row) and their data types (second row).</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>These are the values returned and the data types they represent:</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Value</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>1</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>3</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>4</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>5</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>6</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>7</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>8</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>9</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>10</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>11</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>12</p></td>
</tr>
<tr class="even">
<td><p>NextRow</p></td>
<td><p>The data in the next row in the table or query. When you open a channel, NextRow returns the data in the first row. If the current row is the last record and you run NextRow, the request fails.</p></td>
</tr>
<tr class="odd">
<td><p>PrevRow</p></td>
<td><p>The data in the previous row in the table or query. If PrevRow is the first request on a new channel, the data in the last row of the table or query is returned. If the first record is the current row, the request for PrevRow fails.</p></td>
</tr>
<tr class="even">
<td><p>FirstRow</p></td>
<td><p>The data in the first row of the table or query.</p></td>
</tr>
<tr class="odd">
<td><p>LastRow</p></td>
<td><p>The data in the last row of the table or query.</p></td>
</tr>
<tr class="even">
<td><p>FieldCount</p></td>
<td><p>The number of fields in the table or query.</p></td>
</tr>
<tr class="odd">
<td><p>SQLText</p></td>
<td><p>An SQL statement representing the table or query. For tables, this item returns an SQL statement in the form &quot;SELECT * FROM <em>table</em>;&quot;.</p></td>
</tr>
<tr class="even">
<td><p>SQLText;<em>n</em></p></td>
<td><p>An SQL statement, in <em>n</em>-character chunks, representing the table or query, where <em>n</em> is an integer up to 256. For example, suppose a query is represented by the following SQL statement: The item &quot;SQLText;7&quot; returns the following tab-delimited chunks: The item &quot;SQLText;7&quot; returns the following tab-delimited chunks:</p></td>
</tr>
</tbody>
</table>


The following example shows how you can use DDE in a Visual Basic procedure to request data from a table in the Northwind sample database and insert that data into a text file:

    Sub NorthwindDDE 
        Dim intChan1 As Integer, intChan2 As Integer, intChan3 As Integer 
        Dim strResp1 As Variant, strResp2 As Variant, strResp3 As Variant 
     
        ' In a Visual Basic module, get data from Categories table, 
        ' Catalog query, and Orders table in Northwind.mdb. 
        ' Make sure database is open first. 
        intChan1 = DDEInitiate("MSAccess", "Northwind;TABLE Shippers") 
        intChan2 = DDEInitiate("MSAccess", "Northwind;QUERY Catalog") 
        intChan3 = DDEInitiate("MSAccess", "Northwind;SQL SELECT * " _ 
            & "FROM Orders " _ 
            & "WHERE OrderID > 10050;") 
     
        strResp1 = DDERequest(intChan1, "All") 
        strResp2 = DDERequest(intChan2, "FieldNames;T") 
        strResp3 = DDERequest(intChan3, "FieldNames;T") 
        DDETerminate intChan1 
        DDETerminate intChan2 
        DDETerminate intChan3 
     
        ' Insert data into text file. 
        Open "C:\DATA.TXT" For Append As #1 
        Print #1, strResp1 
        Print #1, strResp2 
        Print #1, strResp3 
        Close #1 
    End Sub

