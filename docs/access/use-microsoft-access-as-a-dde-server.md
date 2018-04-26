---
title: "Use Microsoft Access as a DDE Server"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm5186349
  
localization_priority: Normal
ms.assetid: a3e82bf7-94b5-8eec-86bc-2d5387d66738
description: "Microsoft Access supports dynamic data exchange (DDE) as either a destination (client) application or a source (server) application. For example, an application such as Microsoft Word, acting as a client, can request data through DDE from a Microsoft Access database that's acting as a server."
---

# Use Microsoft Access as a DDE Server

Microsoft Access supports dynamic data exchange (DDE) as either a destination (client) application or a source (server) application. For example, an application such as Microsoft Word, acting as a client, can request data through DDE from a Microsoft Access database that's acting as a server.
  
> [!TIP]
> If you need to manipulate Microsoft Access objects from another application, you may want to consider using Automation. 
  
A DDE conversation between a client and server is established on a particular topic. A topic can be either a data file in the format supported by the server application, or it can be the System topic, which supplies information about the server application itself. Once a conversation has begun on a particular topic, only a data item associated with that topic can be transferred.
  
For example, suppose you are running Microsoft Word and want to insert data from a particular Microsoft Access database into a document. You begin a DDE conversation with Microsoft Access by opening a DDE channel with the **DDEInitiate** function and specifying the database file name as the topic. You can then transfer data from that database to Microsoft Word through that channel. 
  
As a DDE server, Microsoft Access supports the following topics:
  
- The System topic
    
- The name of a database ( *database*  topic) 
    
- The name of a table ( *tablename*  topic) 
    
- The name of a query ( *queryname*  topic) 
    
- A Microsoft Access SQL string ( *sqlstring*  topic) 
    
Once you've established a DDE conversation, you can use the **DDEExecute** statement to send a command from the client to the server application. When used as a DDE server, Microsoft Access recognizes any of the following as a valid command: 
  
- The name of a macro in the current database.
    
- Any action that you can carry out in Visual Basic by using one of the methods of the **DoCmd** object. 
    
- The OpenDatabase and CloseDatabase actions, which are used only for DDE operations. (For an example of how to use these actions, see the example later in this topic.)
    
> [!NOTE]
> When you specify a macro action as a **DDEExecute** statement, the action and any arguments follow the **DoCmd** object syntax and must be enclosed in brackets ([ ]). However, applications that support DDE don't recognize intrinsic constants in DDE operations. Also, string arguments must be enclosed in quotation marks (" ") if the string contains a comma. Otherwise, quotation marks aren't required. 
  
The client application can use the **DDERequest** function to request text data from the server application over an open DDE channel. Or the client can use the **DDEPoke** statement to send data to the server application. Once the data transfer is complete, the client can use the **DDETerminate** statement to close the DDE channel, or the **DDETerminateAll** statement to close all open channels. 
  
> [!NOTE]
> When your client application has finished receiving data over a DDE channel, it should close that channel to conserve memory resources. 
  
The following example demonstrates how to create a Microsoft Word procedure with Visual Basic that uses Microsoft Access as a DDE server. (For this example to work, Microsoft Access must be running.)
  
```
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
        &amp; "QUERY Ten Most Expensive Products") 
    strQueryData = DDERequest(intChan2, "All") 
    DDETerminate intChan2 
 
    ' Close database. 
    DDEExecute intChan1, "[CloseDatabase]" 
    DDETerminate intChan1 
 
    ' Print retrieved data to Debug Window. 
    Debug.Print strQueryData 
End Sub
```

The following sections provide information about the valid DDE topics supported by Microsoft Access.
  
## The System Topic

The System topic is a standard topic for all Microsoft Windows-based applications. It supplies information about the other topics supported by the application. To access this information, your code must first call the **DDEInitiate** function with as the  *topic*  argument, and then execute the **DDERequest** statement with one of the following supplied for the  *item*  argument. 
  
|**Item**|**Returns**|
|:-----|:-----|
|SysItems  <br/> |A list of items supported by the System topic in Microsoft Access.  <br/> |
|Formats  <br/> |A list of the formats Microsoft Access can copy onto the Clipboard.  <br/> |
|Status  <br/> |"Busy" or "Ready".  <br/> |
|Topics  <br/> |A list of all open databases.  <br/> |
   
The following example demonstrates the use of the **DDEInitiate** and **DDERequest** functions with the System topic: 
  
```
' In Visual Basic, initiate DDE conversation with Microsoft Access. 
Dim intChan1 As Integer, strResults As String 
intChan1 = DDEInitiate("MSAccess", "System") 
' Request list of topics supported by System topic. 
strResults = DDERequest(intChan1, "SysItems") 
' Run OpenDatabase action to open Northwind.mdb. 
' You may need to change this path to point to actual location 
' of Northwind sample database. 
DDEExecute intChan1, "[OpenDatabase C:\Access\Samples\Northwind.mdb]"
```

## The

The  *database*  topic is the file name of an existing database. You can type either just the base name (Northwind), or its path and .mdb extension (C:\Access\Samples\Northwind.mdb). After you start a DDE conversation with the database, you can request a list of the objects in that database. 
  
> [!NOTE]
> You can't use DDE to query the Microsoft Access workgroup information file. 
  
The  *database*  topic supports the following items. 
  
|**Item**|**Returns**|
|:-----|:-----|
|TableList  <br/> |A list of tables.  <br/> |
|QueryList  <br/> |A list of queries.  <br/> |
|FormList  <br/> |A list of forms.  <br/> |
|ReportList  <br/> |A list of reports.  <br/> |
|MacroList  <br/> |A list of macros.  <br/> |
|ModuleList  <br/> |A list of modules.  <br/> |
|ViewList  <br/> |A list of views  <br/> |
|StoredProcedureList  <br/> |A list of stored procedures  <br/> |
|DatabaseDiagramList  <br/> |A list of database diagrams  <br/> |
   
The following example shows how you can open the Employees form in the Northwind sample database from a Visual Basic procedure:
  
```
' In Visual Basic, initiate DDE conversation with 
' Northwind sample database. 
' Make sure database is open. 
intChan2 = DDEInitiate("MSAccess", "Northwind") 
' Request list of forms in Northwind sample database. 
strResponse = DDERequest(intChan2, "FormList") 
' Run OpenForm action and arguments to open Employees form. 
DDEExecute intChan2, "[OpenForm Employees,0,,,1,0]"
```

## The TABLE

These topics use the following syntax:
  
 *databasename* **; TABLE** *tablename* 
  
 *databasename* **; QUERY** *queryname* 
  
 *databasename* **; SQL [** *sqlstring* **]**
  
|**Part**|**Description**|
|:-----|:-----|
| *databasename*  <br/> |The name of the database that the table or query is in or that the SQL statement applies to, followed by a semicolon (;). The database name can be just the base name (Northwind) or its full path and .mdb extension (C:\Access\Samples\Northwind.mdb).  <br/> |
| *tablename*  <br/> |The name of an existing table.  <br/> |
| *queryname*  <br/> |The name of an existing query.  <br/> |
| *sqlstring*  <br/> |A valid SQL statement up to 256 characters long, ending with a semicolon. To exchange more than 256 characters, omit this argument and instead use successive **DDEPoke** statements to build an SQL statement. For example, the following Visual Basic code uses the **DDEPoke** statement to build an SQL statement and then request the results of the query.  <br/> |
|||
   
The following table lists the valid items for the TABLE  *tablename*  , QUERY  *queryname*  , and SQL  *sqlstring*  topics. 
  
|**Item**|**Returns**|
|:-----|:-----|
|All  <br/> |All the data in the table, including field names.  <br/> |
|Data  <br/> |All rows of data, without field names.  <br/> |
|FieldNames  <br/> |A single-row list of field names.  <br/> |
|FieldNames;T  <br/> |A two-row list of field names (first row) and their data types (second row).  <br/> |
||These are the values returned and the data types they represent:  <br/> |
||Value  <br/> |Data type  <br/> |
||0  <br/> |Invalid  <br/> |
||1  <br/> |**True** / **False** (non- **Null** )  <br/> |
||2  <br/> |Unsigned byte  <br/> |
||3  <br/> |2-byte signed integer ( **Integer** )  <br/> |
||4  <br/> |4-byte signed integer ( **Long** )  <br/> |
||5  <br/> |8-byte signed integer ( **Currency** )  <br/> |
||6  <br/> |4-byte single-precision floating-point ( **Single** )  <br/> |
||7  <br/> |8-byte double-precision floating-point ( **Double** )  <br/> |
||8  <br/> |Date/Time  <br/> |
||9  <br/> |Binary data, 256 bytes maximum  <br/> |
||10  <br/> |ANSI text, not case-sensitive, 256 bytes maximum (Text)  <br/> |
||11  <br/> |Long binary (OLE Object)  <br/> |
||12  <br/> |Long text (Memo)  <br/> |
|NextRow  <br/> |The data in the next row in the table or query. When you open a channel, NextRow returns the data in the first row. If the current row is the last record and you run NextRow, the request fails.  <br/> |
|PrevRow  <br/> |The data in the previous row in the table or query. If PrevRow is the first request on a new channel, the data in the last row of the table or query is returned. If the first record is the current row, the request for PrevRow fails.  <br/> |
|FirstRow  <br/> |The data in the first row of the table or query.  <br/> |
|LastRow  <br/> |The data in the last row of the table or query.  <br/> |
|FieldCount  <br/> |The number of fields in the table or query.  <br/> |
|SQLText  <br/> |An SQL statement representing the table or query. For tables, this item returns an SQL statement in the form "SELECT * FROM  *table*  ;".  <br/> |
|SQLText; *n*  <br/> |An SQL statement, in  *n*  -character chunks, representing the table or query, where  *n*  is an integer up to 256. For example, suppose a query is represented by the following SQL statement: The item "SQLText;7" returns the following tab-delimited chunks: The item "SQLText;7" returns the following tab-delimited chunks:  <br/> |
   
The following example shows how you can use DDE in a Visual Basic procedure to request data from a table in the Northwind sample database and insert that data into a text file:
  
```
Sub NorthwindDDE 
    Dim intChan1 As Integer, intChan2 As Integer, intChan3 As Integer 
    Dim strResp1 As Variant, strResp2 As Variant, strResp3 As Variant 
 
    ' In a Visual Basic module, get data from Categories table, 
    ' Catalog query, and Orders table in Northwind.mdb. 
    ' Make sure database is open first. 
    intChan1 = DDEInitiate("MSAccess", "Northwind;TABLE Shippers") 
    intChan2 = DDEInitiate("MSAccess", "Northwind;QUERY Catalog") 
    intChan3 = DDEInitiate("MSAccess", "Northwind;SQL SELECT * " _ 
        &amp; "FROM Orders " _ 
        &amp; "WHERE OrderID > 10050;") 
 
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
```


