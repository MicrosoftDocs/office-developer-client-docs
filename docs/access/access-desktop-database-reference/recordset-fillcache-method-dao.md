---
title: Recordset.FillCache Method (DAO)
TOCTitle: FillCache Method
ms:assetid: d171b939-b904-c6bd-6217-68bc2814e282
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff834751(v=office.15)
ms:contentKeyID: 48547861
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset.FillCache Method (DAO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  

Fills all or a part of a local cache for a **Recordset** object that contains data from a Microsoft Access database engine-connected ODBC data source (Microsoft Access database engine-connected ODBC databases only).

## Syntax

*expression* .FillCache(***Rows***, ***StartBookmark***)

*expression* A variable that represents a **Recordset** object.

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
<td><p>Rows</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>A <strong>Variant</strong> (<strong>Integer</strong> subtype) that specifies the number of rows to store in the cache. If you omit this argument, the value is determined by the <strong><a href="recordset-cachesize-property-dao.md">CacheSize</a></strong> property setting.</p></td>
</tr>
<tr class="even">
<td><p>StartBookmark</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>A <strong>Variant</strong> (<strong>String</strong> subtype) that specifies a bookmark. The cache is filled starting from the record indicated by this bookmark. If you omit this argument, the cache is filled starting from the record indicated by the <strong><a href="recordset-cachestart-property-dao.md">CacheStart</a></strong> property.</p></td>
</tr>
</tbody>
</table>


## Remarks

Caching improves the performance of an application that retrieves data from a remote server. A cache is space in local memory that holds the data most recently retrieved from the server; this assumes that the data will probably be requested again while the application is running. When a user requests data, the Microsoft Access database engine checks the cache for the data first rather than retrieving it from the server, which takes more time. The cache doesn't save data that doesn't come from an ODBC data source.

Rather than waiting for the cache to be filled with records as they are retrieved, you can use the **FillCache** method to explicitly fill the cache at any time. This is a faster way to fill the cache because **FillCache** retrieves several records at once instead of one at a time. For example, while you view each screenful of records, your application uses **FillCache** to retrieve the next screenful of records for viewing.

Any Microsoft Access database engine-connected ODBC data source that you access with **Recordset** objects can have a local cache. To create the cache, open a **Recordset** object from the remote data source, and then set the **CacheSize** and **CacheStart** properties of the **Recordset**.

If rows and startbookmark create a range of records that is partially or entirely outside the range of records specified by the **CacheSize** and **CacheStart** properties, the portion of the recordset outside this range is ignored and will not be loaded into the cache.

If **FillCache** requests more records than the number remaining in the remote data source, the Microsoft Access database engine retrieves only the remaining records, and no error occurs.


> [!NOTE]
> <UL>
> <LI>
> <P>Records retrieved from the cache don't reflect concurrent changes that other users made to the source data.</P>
> <LI>
> <P><STRONG>FillCache</STRONG> only retrieves records not already cached. To force an update of all the cached data, set the <STRONG>CacheSize</STRONG> property of the <STRONG>Recordset</STRONG> to 0, reset it to the size of the cache you originally requested, and then use <STRONG>FillCache</STRONG>.</P></LI></UL>



## Example

This example uses the **CreateTableDef** and **FillCache** methods and the **CacheSize**, **CacheStart** and **SourceTableName** properties to enumerate the records in a linked table twice. Then it enumerates the records twice with a 50-record cache. The example then displays the performance statistics for the uncached and cached runs through the linked table.

    Sub ClientServerX3() 
     
       Dim dbsCurrent As Database 
       Dim tdfRoyalties As TableDef 
       Dim rstRemote As Recordset 
       Dim sngStart As Single 
       Dim sngEnd As Single 
       Dim sngNoCache As Single 
       Dim sngCache As Single 
       Dim intLoop As Integer 
       Dim strTemp As String 
       Dim intRecords As Integer 
     
       ' Open a database to which a linked table can be  
       ' appended. 
       Set dbsCurrent = OpenDatabase("DB1.mdb") 
     
       ' Create a linked table that connects to a Microsoft SQL 
       ' Server database. 
       Set tdfRoyalties = _ 
          dbsCurrent.CreateTableDef("Royalties") 
       ' Note: The DSN referenced below must be set to  
       '       use Microsoft Windows NT Authentication Mode to  
       '       authorize user access to the Microsoft SQL Server. 
       tdfRoyalties.Connect = _ 
          "ODBC;DATABASE=pubs;DSN=Publishers" 
       tdfRoyalties.SourceTableName = "roysched" 
       dbsCurrent.TableDefs.Append tdfRoyalties 
       Set rstRemote = _ 
          dbsCurrent.OpenRecordset("Royalties") 
     
       With rstRemote 
          ' Enumerate the Recordset object twice and record 
          ' the elapsed time. 
          sngStart = Timer 
     
          For intLoop = 1 To 2 
             .MoveFirst 
             Do While Not .EOF 
                ' Execute a simple operation for the 
                ' performance test. 
                strTemp = !title_id 
                .MoveNext 
             Loop 
          Next intLoop 
     
          sngEnd = Timer 
          sngNoCache = sngEnd - sngStart 
     
          ' Cache the first 50 records. 
          .MoveFirst 
          .CacheSize = 50 
          .FillCache 
          sngStart = Timer 
     
          ' Enumerate the Recordset object twice and record 
          ' the elapsed time. 
          For intLoop = 1 To 2 
             intRecords = 0 
             .MoveFirst 
             Do While Not .EOF 
                ' Execute a simple operation for the 
                ' performance test. 
                strTemp = !title_id 
                ' Count the records. If the end of the 
                ' cache is reached, reset the cache to the 
                ' next 50 records. 
                intRecords = intRecords + 1 
                .MoveNext 
                If intRecords Mod 50 = 0 Then 
                   .CacheStart = .Bookmark 
                   .FillCache 
                End If 
             Loop 
          Next intLoop 
     
          sngEnd = Timer 
          sngCache = sngEnd - sngStart 
     
          ' Display performance results. 
          MsgBox "Caching Performance Results:" & vbCr & _ 
             "  No cache: " & Format(sngNoCache, _ 
             "##0.000") & " seconds" & vbCr & _ 
             "  50-record cache: " & Format(sngCache, _ 
             "##0.000") & " seconds" 
          .Close 
       End With 
     
       ' Delete linked table because this is a demonstration. 
       dbsCurrent.TableDefs.Delete tdfRoyalties.Name 
       dbsCurrent.Close 
     
    End Sub

