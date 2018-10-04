---
title: Microsoft OLE DB Provider for SQL Server
TOCTitle: Microsoft OLE DB Provider for SQL Server
ms:assetid: 0ffdea03-1a76-499b-f649-423f6b3c13d7
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248868(v=office.15)
ms:contentKeyID: 48543282
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Microsoft OLE DB Provider for SQL Server


**Applies to**: Access 2013 | Office 2013

**In this article**  
Connection String Parameters  
Typical Connection String  
Provider-Specific Connection Parameters  
Command Object Usage  
Stored Procedures  
ODBC SQL  
Transact-SQL  
Recordset Behavior  
Dynamic Properties  
Connection Dynamic Properties  
Recordset Dynamic Properties  
Command Dynamic Properties  

The Microsoft OLE DB Provider for SQL Server, SQLOLEDB, allows ADO to access Microsoft SQL Server.

## Connection String Parameters

To connect to this provider, set the *Provider* argument to the [ConnectionString](connectionstring-property-ado.md) property to:

``` 
 
SQLOLEDB 
```

This value can also be set or read using the [Provider](provider-property-ado.md) property.

## Typical Connection String

A typical connection string for this provider is:

``` 
 
"Provider=SQLOLEDB;Data Source=serverName;" 
Initial Catalog=databaseName; 
User ID=userName;Password=userPassword;" 
```

The string consists of these keywords:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Provider</strong></p></td>
<td><p>Specifies the OLE DB Provider for SQL Server.</p></td>
</tr>
<tr class="even">
<td><p><strong>Data Source</strong> or <strong>Server</strong></p></td>
<td><p>Specifies the name of a server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Initial Catalog</strong> or <strong>Database</strong></p></td>
<td><p>Specifies the name of a database on the server.</p></td>
</tr>
<tr class="even">
<td><p><strong>User ID</strong> or <strong>uid</strong></p></td>
<td><p>Specifies the user name (for SQL Server Authentication).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Password</strong> or <strong>pwd</strong></p></td>
<td><p>Specifies the user password (for SQL Server Authentication).</p></td>
</tr>
</tbody>
</table>


## Provider-Specific Connection Parameters

The provider supports several provider-specific connection parameters in addition to those defined by ADO. As with the ADO connection properties, these provider-specific properties can be set via the [Properties](properties-collection-ado.md) collection of a [Connection](connection-object-ado.md) or can be set as part of the **ConnectionString**.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Trusted_Connection</p></td>
<td><p>Indicates the user authentication mode. This can be set to <strong>Yes</strong> or <strong>No</strong>. The default value is <strong>No</strong>. If this property is set to <strong>Yes</strong>, then SQLOLEDB uses Microsoft Windows NT Authentication Mode to authorize user access to the SQL Server database specified by the <strong>Location</strong> and <a href="datasource-property-ado.md">Datasource</a> property values. If this property is set to <strong>No</strong>, then SQLOLEDB uses Mixed Mode to authorize user access to the SQL Server database. The SQL Server login and password are specified in the <strong>User Id</strong> and <strong>Password</strong> properties.</p></td>
</tr>
<tr class="even">
<td><p>Current Language</p></td>
<td><p>Indicates a SQL Server language name. Identifies the language used for system message selection and formatting. The language must be installed on the SQL Server, otherwise opening the connection will fail.</p></td>
</tr>
<tr class="odd">
<td><p>Network Address</p></td>
<td><p>Indicates the network address of the SQL Server specified by the <strong>Location</strong> property.</p></td>
</tr>
<tr class="even">
<td><p>Network Library</p></td>
<td><p>Indicates the name of the network library (dynamic-link libraries) used to communicate with the SQL Server. The name should not include the path or the .dll file name extension. The default is provided by the SQL Server client configuration.</p></td>
</tr>
<tr class="odd">
<td><p>Use Procedure for Prepare</p></td>
<td><p>Determines whether SQL Server creates temporary stored procedures when Commands are prepared (by the <strong>Prepared</strong> property).</p></td>
</tr>
<tr class="even">
<td><p>Auto Translate</p></td>
<td><p>Indicates whether OEM/ANSI characters are converted. This property can be set to <strong>True</strong> or <strong>False</strong>. The default value is <strong>True</strong>. If this property is set to <strong>True</strong>, then SQLOLEDB performs OEM/ANSI character conversion when multi-byte character strings are retrieved from, or sent to, the SQL Server. If this property is set to <strong>False</strong>, then SQLOLEDB does not perform OEM/ANSI character conversion on multi-byte character string data.</p></td>
</tr>
<tr class="odd">
<td><p>Packet Size</p></td>
<td><p>Indicates a network packet size in bytes. The packet size property value must be between 512 and 32767. The default SQLOLEDB network packet size is 4096.</p></td>
</tr>
<tr class="even">
<td><p>Application Name</p></td>
<td><p>Indicates the client application name.</p></td>
</tr>
<tr class="odd">
<td><p>Workstation ID</p></td>
<td><p>A string identifying the workstation.</p></td>
</tr>
</tbody>
</table>


## Command Object Usage

SQLOLEDB accepts an amalgam of ODBC, ANSI, and SQL Server-specific Transact-SQL as valid syntax. For example, the following SQL statement uses an ODBC SQL escape sequence to specify the LCASE string function:

``` 
 
SELECT customerid={fn LCASE(CustomerID)} FROM Customers 
```

LCASE returns a character string, converting all uppercase characters to their lowercase equivalents. The ANSI SQL string function LOWER performs the same operation, so the following SQL statement is an ANSI equivalent to the ODBC statement presented above:

``` 
 
SELECT customerid=LOWER(CustomerID) FROM Customers 
```

SQLOLEDB successfully processes either form of the statement when specified as text for a command.

## Stored Procedures

When executing a SQL Server stored procedure using a SQLOLEDB command, use the ODBC procedure call escape sequence in the command text. SQLOLEDB then uses the remote procedure call mechanism of SQL Server to optimize command processing. For example, the following ODBC SQL statement is the preferred command text over the Transact-SQL form:

## ODBC SQL

``` 
 
{call SalesByCategory('Produce', '1995')} 
```

## Transact-SQL

``` 
 
EXECUTE SalesByCategory 'Produce', '1995' 
```

## Recordset Behavior

SQLOLEDB cannot use SQL Server cursors to support the multiple-result generated by many commands. If a consumer requests a recordset requiring SQL Server cursor support, an error occurs if the command text used generates more than a single recordset as its result.

Scrollable SQLOLEDB recordsets are supported by SQL Server cursors. SQL Server imposes limitations on cursors that are sensitive to changes made by other users of the database. Specifically, the rows in some cursors cannot be ordered, and attempting to create a recordset using a command containing an SQL ORDER BY clause can fail.

## Dynamic Properties

The Microsoft OLE DB Provider for SQL Server inserts several dynamic properties into the **Properties** collection of the unopened [Connection](connection-object-ado.md), [Recordset](recordset-object-ado.md), and [Command](command-object-ado.md) objects.

The following tables are a cross-index of the ADO and OLE DB names for each dynamic property. The OLE DB Programmer's Reference refers to an ADO property name by the term "Description." You can find more information about these properties in the OLE DB Programmer's Reference. Search for the OLE DB property name in the Index or see Appendix C: OLE DB Properties.

## Connection Dynamic Properties

The following properties are added to the **Connection** object's **Properties** collection.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>ADO Property Name</p></th>
<th><p>OLE DB Property Name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Active Sessions</p></td>
<td><p>DBPROP_ACTIVESESSIONS</p></td>
</tr>
<tr class="even">
<td><p>Asynchable Abort</p></td>
<td><p>DBPROP_ASYNCTXNABORT</p></td>
</tr>
<tr class="odd">
<td><p>Asynchable Commit</p></td>
<td><p>DBPROP_ASYNCTNXCOMMIT</p></td>
</tr>
<tr class="even">
<td><p>Autocommit Isolation Levels</p></td>
<td><p>DBPROP_SESS_AUTOCOMMITISOLEVELS</p></td>
</tr>
<tr class="odd">
<td><p>Catalog Location</p></td>
<td><p>DBPROP_CATALOGLOCATION</p></td>
</tr>
<tr class="even">
<td><p>Catalog Term</p></td>
<td><p>DBPROP_CATALOGTERM</p></td>
</tr>
<tr class="odd">
<td><p>Column Definition</p></td>
<td><p>DBPROP_COLUMNDEFINITION</p></td>
</tr>
<tr class="even">
<td><p>Connect Timeout</p></td>
<td><p>DBPROP_INIT_TIMEOUT</p></td>
</tr>
<tr class="odd">
<td><p>Current Catalog</p></td>
<td><p>DBPROP_CURRENTCATALOG</p></td>
</tr>
<tr class="even">
<td><p>Data Source</p></td>
<td><p>DBPROP_INIT_DATASOURCE</p></td>
</tr>
<tr class="odd">
<td><p>Data Source Name</p></td>
<td><p>DBPROP_DATASOURCENAME</p></td>
</tr>
<tr class="even">
<td><p>Data Source Object Threading Model</p></td>
<td><p>DBPROP_DSOTHREADMODEL</p></td>
</tr>
<tr class="odd">
<td><p>DBMS Name</p></td>
<td><p>DBPROP_DBMSNAME</p></td>
</tr>
<tr class="even">
<td><p>DBMS Version</p></td>
<td><p>DBPROP_DBMSVER</p></td>
</tr>
<tr class="odd">
<td><p>Extended Properties</p></td>
<td><p>DBPROP_INIT_PROVIDERSTRING</p></td>
</tr>
<tr class="even">
<td><p>GROUP BY Support</p></td>
<td><p>DBPROP_GROUPBY</p></td>
</tr>
<tr class="odd">
<td><p>Heterogeneous Table Support</p></td>
<td><p>DBPROP_HETEROGENEOUSTABLES</p></td>
</tr>
<tr class="even">
<td><p>Identifier Case Sensitivity</p></td>
<td><p>DBPROP_IDENTIFIERCASE</p></td>
</tr>
<tr class="odd">
<td><p>Initial Catalog</p></td>
<td><p>DBPROP_INIT_CATALOG</p></td>
</tr>
<tr class="even">
<td><p>Isolation Levels</p></td>
<td><p>DBPROP_SUPPORTEDTXNISOLEVELS</p></td>
</tr>
<tr class="odd">
<td><p>Isolation Retention</p></td>
<td><p>DBPROP_SUPPORTEDTXNISORETAIN</p></td>
</tr>
<tr class="even">
<td><p>Locale Identifier</p></td>
<td><p>DBPROP_INIT_LCID</p></td>
</tr>
<tr class="odd">
<td><p>Maximum Index Size</p></td>
<td><p>DBPROP_MAXINDEXSIZE</p></td>
</tr>
<tr class="even">
<td><p>Maximum Row Size</p></td>
<td><p>DBPROP_MAXROWSIZE</p></td>
</tr>
<tr class="odd">
<td><p>Maximum Row Size Includes BLOB</p></td>
<td><p>DBPROP_MAXROWSIZEINCLUDESBLOB</p></td>
</tr>
<tr class="even">
<td><p>Maximum Tables in SELECT</p></td>
<td><p>DBPROP_MAXTABLESINSELECT</p></td>
</tr>
<tr class="odd">
<td><p>Multiple Parameter Sets</p></td>
<td><p>DBPROP_MULTIPLEPARAMSETS</p></td>
</tr>
<tr class="even">
<td><p>Multiple Results</p></td>
<td><p>DBPROP_MULTIPLERESULTS</p></td>
</tr>
<tr class="odd">
<td><p>Multiple Storage Objects</p></td>
<td><p>DBPROP_MULTIPLESTORAGEOBJECTS</p></td>
</tr>
<tr class="even">
<td><p>Multi-Table Update</p></td>
<td><p>DBPROP_MULTITABLEUPDATE</p></td>
</tr>
<tr class="odd">
<td><p>NULL Collation Order</p></td>
<td><p>DBPROP_NULLCOLLATION</p></td>
</tr>
<tr class="even">
<td><p>NULL Concatenation Behavior</p></td>
<td><p>DBPROP_CONCATNULLBEHAVIOR</p></td>
</tr>
<tr class="odd">
<td><p>OLE DB Version</p></td>
<td><p>DBPROP_PROVIDEROLEDBVER</p></td>
</tr>
<tr class="even">
<td><p>OLE Object Support</p></td>
<td><p>DBPROP_OLEOBJECTS</p></td>
</tr>
<tr class="odd">
<td><p>Open Rowset Support</p></td>
<td><p>DBPROP_OPENROWSETSUPPORT</p></td>
</tr>
<tr class="even">
<td><p>ORDER BY Columns in Select List</p></td>
<td><p>DBPROP_ORDERBYCOLUMNSINSELECT</p></td>
</tr>
<tr class="odd">
<td><p>Output Parameter Availability</p></td>
<td><p>DBPROP_OUTPUTPARAMETERAVAILABILITY</p></td>
</tr>
<tr class="even">
<td><p>Pass By Ref Accessors</p></td>
<td><p>DBPROP_BYREFACCESSORS</p></td>
</tr>
<tr class="odd">
<td><p>Password</p></td>
<td><p>DBPROP_AUTH_PASSWORD</p></td>
</tr>
<tr class="even">
<td><p>Persist Security Info</p></td>
<td><p>DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO</p></td>
</tr>
<tr class="odd">
<td><p>Persistent ID Type</p></td>
<td><p>DBPROP_PERSISTENTIDTYPE</p></td>
</tr>
<tr class="even">
<td><p>Prepare Abort Behavior</p></td>
<td><p>DBPROP_PREPAREABORTBEHAVIOR</p></td>
</tr>
<tr class="odd">
<td><p>Prepare Commit Behavior</p></td>
<td><p>DBPROP_PREPARECOMMITBEHAVIOR</p></td>
</tr>
<tr class="even">
<td><p>Procedure Term</p></td>
<td><p>DBPROP_PROCEDURETERM</p></td>
</tr>
<tr class="odd">
<td><p>Prompt</p></td>
<td><p>DBPROP_INIT_PROMPT</p></td>
</tr>
<tr class="even">
<td><p>Provider Friendly Name</p></td>
<td><p>DBPROP_PROVIDERFRIENDLYNAME</p></td>
</tr>
<tr class="odd">
<td><p>Provider Name</p></td>
<td><p>DBPROP_PROVIDERFILENAME</p></td>
</tr>
<tr class="even">
<td><p>Provider Version</p></td>
<td><p>DBPROP_PROVIDERVER</p></td>
</tr>
<tr class="odd">
<td><p>Read-Only Data Source</p></td>
<td><p>DBPROP_DATASOURCEREADONLY</p></td>
</tr>
<tr class="even">
<td><p>Rowset Conversions on Command</p></td>
<td><p>DBPROP_ROWSETCONVERSIONSONCOMMAND</p></td>
</tr>
<tr class="odd">
<td><p>Schema Term</p></td>
<td><p>DBPROP_SCHEMATERM</p></td>
</tr>
<tr class="even">
<td><p>Schema Usage</p></td>
<td><p>DBPROP_SCHEMAUSAGE</p></td>
</tr>
<tr class="odd">
<td><p>SQL Support</p></td>
<td><p>DBPROP_SQLSUPPORT</p></td>
</tr>
<tr class="even">
<td><p>Structured Storage</p></td>
<td><p>DBPROP_STRUCTUREDSTORAGE</p></td>
</tr>
<tr class="odd">
<td><p>Subquery Support</p></td>
<td><p>DBPROP_SUBQUERIES</p></td>
</tr>
<tr class="even">
<td><p>Table Term</p></td>
<td><p>DBPROP_TABLETERM</p></td>
</tr>
<tr class="odd">
<td><p>Transaction DDL</p></td>
<td><p>DBPROP_SUPPORTEDTXNDDL</p></td>
</tr>
<tr class="even">
<td><p>User ID</p></td>
<td><p>DBPROP_AUTH_USERID</p></td>
</tr>
<tr class="odd">
<td><p>User Name</p></td>
<td><p>DBPROP_USERNAME</p></td>
</tr>
<tr class="even">
<td><p>Window Handle</p></td>
<td><p>DBPROP_INIT_HWND</p></td>
</tr>
</tbody>
</table>


## Recordset Dynamic Properties

The following properties are added to the **Recordset** object's **Properties** collection.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>ADO Property Name</p></th>
<th><p>OLE DB Property Name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Access Order</p></td>
<td><p>DBPROP_ACCESSORDER</p></td>
</tr>
<tr class="even">
<td><p>Blocking Storage Objects</p></td>
<td><p>DBPROP_BLOCKINGSTORAGEOBJECTS</p></td>
</tr>
<tr class="odd">
<td><p>Bookmark Type</p></td>
<td><p>DBPROP_BOOKMARKTYPE</p></td>
</tr>
<tr class="even">
<td><p>Bookmarkable</p></td>
<td><p>DBPROP_IROWSETLOCATE</p></td>
</tr>
<tr class="odd">
<td><p>Change Inserted Rows</p></td>
<td><p>DBPROP_CHANGEINSERTEDROWS</p></td>
</tr>
<tr class="even">
<td><p>Column Privileges</p></td>
<td><p>DBPROP_COLUMNRESTRICT</p></td>
</tr>
<tr class="odd">
<td><p>Column Set Notification</p></td>
<td><p>DBPROP_NOTIFYCOLUMNSET</p></td>
</tr>
<tr class="even">
<td><p>Command Time Out</p></td>
<td><p>DBPROP_COMMANDTIMEOUT</p></td>
</tr>
<tr class="odd">
<td><p>Defer Column</p></td>
<td><p>DBPROP_DEFERRED</p></td>
</tr>
<tr class="even">
<td><p>Delay Storage Object Updates</p></td>
<td><p>DBPROP_DELAYSTORAGEOBJECTS</p></td>
</tr>
<tr class="odd">
<td><p>Fetch Backwards</p></td>
<td><p>DBPROP_CANFETCHBACKWARDS</p></td>
</tr>
<tr class="even">
<td><p>Hold Rows</p></td>
<td><p>DBPROP_CANHOLDROWS</p></td>
</tr>
<tr class="odd">
<td><p>IAccessor</p></td>
<td><p>DBPROP_IAccessor</p></td>
</tr>
<tr class="even">
<td><p>IColumnsInfo</p></td>
<td><p>DBPROP_IColumnsInfo</p></td>
</tr>
<tr class="odd">
<td><p>IColumnsRowset</p></td>
<td><p>DBPROP_IColumnsRowset</p></td>
</tr>
<tr class="even">
<td><p>IConnectionPointContainer</p></td>
<td><p>DBPROP_IConnectionPointContainer</p></td>
</tr>
<tr class="odd">
<td><p>IConvertType</p></td>
<td><p>DBPROP_IConvertType</p></td>
</tr>
<tr class="even">
<td><p>Immobile Rows</p></td>
<td><p>DBPROP_IMMOBILEROWS</p></td>
</tr>
<tr class="odd">
<td><p>IRowset</p></td>
<td><p>DBPROP_IRowset</p></td>
</tr>
<tr class="even">
<td><p>IRowsetChange</p></td>
<td><p>DBPROP_IRowsetChange</p></td>
</tr>
<tr class="odd">
<td><p>IRowsetIdentity</p></td>
<td><p>DBPROP_IRowsetIdentity</p></td>
</tr>
<tr class="even">
<td><p>IRowsetInfo</p></td>
<td><p>DBPROP_IRowsetInfo</p></td>
</tr>
<tr class="odd">
<td><p>IRowsetLocate</p></td>
<td><p>DBPROP_IRowsestLocate</p></td>
</tr>
<tr class="even">
<td><p>IRowsetResynch</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>IRowsetScroll</p></td>
<td><p>DBPROP_IRowsetScroll</p></td>
</tr>
<tr class="even">
<td><p>IRowsetUpdate</p></td>
<td><p>DBPROP_IRowsetUpdate</p></td>
</tr>
<tr class="odd">
<td><p>ISequentialStream</p></td>
<td><p>DBPROP_ISequentialStream</p></td>
</tr>
<tr class="even">
<td><p>ISupportErrorInfo</p></td>
<td><p>DBPROP_ISupportErrorInfo</p></td>
</tr>
<tr class="odd">
<td><p>Literal Bookmarks</p></td>
<td><p>DBPROP_LITERALBOOKMARKS</p></td>
</tr>
<tr class="even">
<td><p>Literal Row Identity</p></td>
<td><p>DBPROP_LITERALIDENTITY</p></td>
</tr>
<tr class="odd">
<td><p>Maximum Open Rows</p></td>
<td><p>DBPROP_MAXOPENROWS</p></td>
</tr>
<tr class="even">
<td><p>Maximum Pending Rows</p></td>
<td><p>DBPROP_MAXPENDINGROWS</p></td>
</tr>
<tr class="odd">
<td><p>Maximum Rows</p></td>
<td><p>DBPROP_MAXROWS</p></td>
</tr>
<tr class="even">
<td><p>Notification Granularity</p></td>
<td><p>DBPROP_NOTIFICATIONGRANULARITY</p></td>
</tr>
<tr class="odd">
<td><p>Notification Phases</p></td>
<td><p>DBPROP_NOTIFICATIONPHASES</p></td>
</tr>
<tr class="even">
<td><p>Objects Transacted</p></td>
<td><p>DBPROP_TRANSACTEDOBJECT</p></td>
</tr>
<tr class="odd">
<td><p>Others' Changes Visible</p></td>
<td><p>DBPROP_OTHERUPDATEDELETE</p></td>
</tr>
<tr class="even">
<td><p>Others' Inserts Visible</p></td>
<td><p>DBPROP_OTHERINSERT</p></td>
</tr>
<tr class="odd">
<td><p>Own Changes Visible</p></td>
<td><p>DBPROP_OWNUPDATEDELETE</p></td>
</tr>
<tr class="even">
<td><p>Own Inserts Visible</p></td>
<td><p>DBPROP_OWNINSERT</p></td>
</tr>
<tr class="odd">
<td><p>Preserve on Abort</p></td>
<td><p>DBPROP_ABORTPRESERVE</p></td>
</tr>
<tr class="even">
<td><p>Preserve on Commit</p></td>
<td><p>DBPROP_COMMITPRESERVE</p></td>
</tr>
<tr class="odd">
<td><p>Quick Restart</p></td>
<td><p>DBPROP_QUICKRESTART</p></td>
</tr>
<tr class="even">
<td><p>Reentrant Events</p></td>
<td><p>DBPROP_REENTRANTEVENTS</p></td>
</tr>
<tr class="odd">
<td><p>Remove Deleted Rows</p></td>
<td><p>DBPROP_REMOVEDELETED</p></td>
</tr>
<tr class="even">
<td><p>Report Multiple Changes</p></td>
<td><p>DBPROP_REPORTMULTIPLECHANGES</p></td>
</tr>
<tr class="odd">
<td><p>Return Pending Inserts</p></td>
<td><p>DBPROP_RETURNPENDINGINSERTS</p></td>
</tr>
<tr class="even">
<td><p>Row Delete Notification</p></td>
<td><p>DBPROP_NOTIFYROWDELETE</p></td>
</tr>
<tr class="odd">
<td><p>Row First Change Notification</p></td>
<td><p>DBPROP_NOTIFYROWFIRSTCHANGE</p></td>
</tr>
<tr class="even">
<td><p>Row Insert Notification</p></td>
<td><p>DBPROP_NOTIFYROWINSERT</p></td>
</tr>
<tr class="odd">
<td><p>Row Privileges</p></td>
<td><p>DBPROP_ROWRESTRICT</p></td>
</tr>
<tr class="even">
<td><p>Row Resynchronization Notification</p></td>
<td><p>DBPROP_NOTIFYROWRESYNCH</p></td>
</tr>
<tr class="odd">
<td><p>Row Threading Model</p></td>
<td><p>DBPROP_ROWTHREADMODEL</p></td>
</tr>
<tr class="even">
<td><p>Row Undo Change Notification</p></td>
<td><p>DBPROP_NOTIFYROWUNDOCHANGE</p></td>
</tr>
<tr class="odd">
<td><p>Row Undo Delete Notification</p></td>
<td><p>DBPROP_NOTIFYROWUNDODELETE</p></td>
</tr>
<tr class="even">
<td><p>Row Undo Insert Notification</p></td>
<td><p>DBPROP_NOTIFYROWUNDOINSERT</p></td>
</tr>
<tr class="odd">
<td><p>Row Update Notification</p></td>
<td><p>DBPROP_NOTIFYROWUPDATE</p></td>
</tr>
<tr class="even">
<td><p>Rowset Fetch Position Change Notification</p></td>
<td><p>DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE</p></td>
</tr>
<tr class="odd">
<td><p>Rowset Release Notification</p></td>
<td><p>DBPROP_NOTIFYROWSETRELEASE</p></td>
</tr>
<tr class="even">
<td><p>Scroll Backwards</p></td>
<td><p>DBPROP_CANSCROLLBACKWARDS</p></td>
</tr>
<tr class="odd">
<td><p>Server Cursor</p></td>
<td><p>DBPROP_SERVERCURSOR</p></td>
</tr>
<tr class="even">
<td><p>Skip Deleted Bookmarks</p></td>
<td><p>DBPROP_BOOKMARKSKIPPED</p></td>
</tr>
<tr class="odd">
<td><p>Strong Row Identity</p></td>
<td><p>DBPROP_STRONGITDENTITY</p></td>
</tr>
<tr class="even">
<td><p>Unique Rows</p></td>
<td><p>DBPROP_UNIQUEROWS</p></td>
</tr>
<tr class="odd">
<td><p>Updatability</p></td>
<td><p>DBPROP_UPDATABILITY</p></td>
</tr>
<tr class="even">
<td><p>Use Bookmarks</p></td>
<td><p>DBPROP_BOOKMARKS</p></td>
</tr>
</tbody>
</table>


## Command Dynamic Properties

The following properties are added to the **Command** object's **Properties** collection.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>ADO Property Name</p></th>
<th><p>OLE DB Property Name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Access Order</p></td>
<td><p>DBPROP_ACCESSORDER</p></td>
</tr>
<tr class="even">
<td><p>Base Path</p></td>
<td><p>SSPROP_STREAM_BASEPATH</p></td>
</tr>
<tr class="odd">
<td><p>Blocking Storage Objects</p></td>
<td><p>DBPROP_BLOCKINGSTORAGEOBJECTS</p></td>
</tr>
<tr class="even">
<td><p>Bookmark Type</p></td>
<td><p>DBPROP_BOOKMARKTYPE</p></td>
</tr>
<tr class="odd">
<td><p>Bookmarkable</p></td>
<td><p>DBPROP_IROWSETLOCATE</p></td>
</tr>
<tr class="even">
<td><p>Change Inserted Rows</p></td>
<td><p>DBPROP_CHANGEINSERTEDROWS</p></td>
</tr>
<tr class="odd">
<td><p>Column Privileges</p></td>
<td><p>DBPROP_COLUMNRESTRICT</p></td>
</tr>
<tr class="even">
<td><p>Column Set Notification</p></td>
<td><p>DBPROP_NOTIFYCOLUMNSET</p></td>
</tr>
<tr class="odd">
<td><p>Content Type</p></td>
<td><p>SSPROP_STREAM_CONTENTTYPE</p></td>
</tr>
<tr class="even">
<td><p>Cursor Auto Fetch</p></td>
<td><p>SSPROP_CURSORAUTOFETCH</p></td>
</tr>
<tr class="odd">
<td><p>Defer Column</p></td>
<td><p>DBPROP_DEFERRED</p></td>
</tr>
<tr class="even">
<td><p>Defer Prepare</p></td>
<td><p>SSPROP_DEFERPREPARE</p></td>
</tr>
<tr class="odd">
<td><p>Delay Storage Object Updates</p></td>
<td><p>DBPROP_DELAYSTORAGEOBJECTS</p></td>
</tr>
<tr class="even">
<td><p>Fetch Backwards</p></td>
<td><p>DBPROP_CANFETCHBACKWARDS</p></td>
</tr>
<tr class="odd">
<td><p>Hold Rows</p></td>
<td><p>DBPROP_CANHOLDROWS</p></td>
</tr>
<tr class="even">
<td><p>IAccessor</p></td>
<td><p>DBPROP_IAccessor</p></td>
</tr>
<tr class="odd">
<td><p>IColumnsInfo</p></td>
<td><p>DBPROP_IColumnsInfo</p></td>
</tr>
<tr class="even">
<td><p>IColumnsRowset</p></td>
<td><p>DBPROP_IColumnsRowset</p></td>
</tr>
<tr class="odd">
<td><p>IConnectionPointContainer</p></td>
<td><p>DBPROP_IConnectionPointContainer</p></td>
</tr>
<tr class="even">
<td><p>IConvertType</p></td>
<td><p>DBPROP_IConvertType</p></td>
</tr>
<tr class="odd">
<td><p>Immobile Rows</p></td>
<td><p>DBPROP_IMMOBILEROWS</p></td>
</tr>
<tr class="even">
<td><p>IRowset</p></td>
<td><p>DBPROP_IRowset</p></td>
</tr>
<tr class="odd">
<td><p>IRowsetChange</p></td>
<td><p>DBPROP_IRowsetChange</p></td>
</tr>
<tr class="even">
<td><p>IRowsetIdentity</p></td>
<td><p>DBPROP_IRowsetIdentity</p></td>
</tr>
<tr class="odd">
<td><p>IRowsetInfo</p></td>
<td><p>DBPROP_IRowsetInfo</p></td>
</tr>
<tr class="even">
<td><p>IRowsetLocate</p></td>
<td><p>DBPROP_IRowsetLocate</p></td>
</tr>
<tr class="odd">
<td><p>IRowsetResynch</p></td>
<td><p>DBPROP_IRowsetResynch</p></td>
</tr>
<tr class="even">
<td><p>IRowsetScroll</p></td>
<td><p>DBPROP_IRowsetScroll</p></td>
</tr>
<tr class="odd">
<td><p>IRowsetUpdate</p></td>
<td><p>DBPROP_IRowsetUpdate</p></td>
</tr>
<tr class="even">
<td><p>ISequentialStream</p></td>
<td><p>DBPROP_ISequentialStream</p></td>
</tr>
<tr class="odd">
<td><p>ISupportErrorInfo</p></td>
<td><p>DBPROP_ISupportErrorInfo</p></td>
</tr>
<tr class="even">
<td><p>Literal Bookmarks</p></td>
<td><p>DBPROP_LITERALBOOKMARKS</p></td>
</tr>
<tr class="odd">
<td><p>Literal Row Identity</p></td>
<td><p>DBPROP_LITERALIDENTITY</p></td>
</tr>
<tr class="even">
<td><p>Lock Mode</p></td>
<td><p>DBPROP_LOCKMODE</p></td>
</tr>
<tr class="odd">
<td><p>Maximum Open Rows</p></td>
<td><p>DBPROP_MAXOPENROWS</p></td>
</tr>
<tr class="even">
<td><p>Maximum Pending Rows</p></td>
<td><p>DBPROP_MAXPENDINGROWS</p></td>
</tr>
<tr class="odd">
<td><p>Maximum Rows</p></td>
<td><p>DBPROP_MAXROWS</p></td>
</tr>
<tr class="even">
<td><p>Notification Granularity</p></td>
<td><p>DBPROP_NOTIFICATIONGRANULARITY</p></td>
</tr>
<tr class="odd">
<td><p>Notification Phases</p></td>
<td><p>DBPROP_NOTIFICATIONPHASES</p></td>
</tr>
<tr class="even">
<td><p>Objects Transacted</p></td>
<td><p>DBPROP_TRANSACTEDOBJECT</p></td>
</tr>
<tr class="odd">
<td><p>Others' Changes Visible</p></td>
<td><p>DBPROP_OTHERUPDATEDELETE</p></td>
</tr>
<tr class="even">
<td><p>Others' Inserts Visible</p></td>
<td><p>DBPROP_OTHERINSERT</p></td>
</tr>
<tr class="odd">
<td><p>Output Encoding Property</p></td>
<td><p>DBPROP_OUTPUTENCODING</p></td>
</tr>
<tr class="even">
<td><p>Output Stream Property</p></td>
<td><p>DBPROP_OUTPUTSTREAM</p></td>
</tr>
<tr class="odd">
<td><p>Own Changes Visible</p></td>
<td><p>DBPROP_OWNUPDATEDELETE</p></td>
</tr>
<tr class="even">
<td><p>Own Inserts Visible</p></td>
<td><p>DBPROP_OWNINSERT</p></td>
</tr>
<tr class="odd">
<td><p>Preserve on Abort</p></td>
<td><p>DBPROP_ABORTPRESERVE</p></td>
</tr>
<tr class="even">
<td><p>Preserve on Commit</p></td>
<td><p>DBPROP_COMMITPRESERVE</p></td>
</tr>
<tr class="odd">
<td><p>Quick Restart</p></td>
<td><p>DBPROP_QUICKRESTART</p></td>
</tr>
<tr class="even">
<td><p>Reentrant Events</p></td>
<td><p>DBPROP_REENTRANTEVENTS</p></td>
</tr>
<tr class="odd">
<td><p>Remove Deleted Rows</p></td>
<td><p>DBPROP_REMOVEDELETED</p></td>
</tr>
<tr class="even">
<td><p>Report Multiple Changes</p></td>
<td><p>DBPROP_REPORTMULTIPLECHANGES</p></td>
</tr>
<tr class="odd">
<td><p>Return Pending Inserts</p></td>
<td><p>DBPROP_RETURNPENDINGINSERTS</p></td>
</tr>
<tr class="even">
<td><p>Row Delete Notification</p></td>
<td><p>DBPROP_NOTIFYROWDELETE</p></td>
</tr>
<tr class="odd">
<td><p>Row First Change Notification</p></td>
<td><p>DBPROP_NOTIFYROWFIRSTCHANGE</p></td>
</tr>
<tr class="even">
<td><p>Row Insert Notification</p></td>
<td><p>DBPROP_NOTIFYROWINSERT</p></td>
</tr>
<tr class="odd">
<td><p>Row Privileges</p></td>
<td><p>DBPROP_ROWRESTRICT</p></td>
</tr>
<tr class="even">
<td><p>Row Resynchronization Notification</p></td>
<td><p>DBPROP_NOTIFYROWRESYNCH</p></td>
</tr>
<tr class="odd">
<td><p>Row Threading Model</p></td>
<td><p>DBPROP_ROWTHREADMODEL</p></td>
</tr>
<tr class="even">
<td><p>Row Undo Change Notification</p></td>
<td><p>DBPROP_NOTIFYROWUNDOCHANGE</p></td>
</tr>
<tr class="odd">
<td><p>Row Undo Delete Notification</p></td>
<td><p>DBPROP_NOTIFYROWUNDODELETE</p></td>
</tr>
<tr class="even">
<td><p>Row Undo Insert Notification</p></td>
<td><p>DBPROP_NOTIFYROWUNDOINSERT</p></td>
</tr>
<tr class="odd">
<td><p>Row Update Notification</p></td>
<td><p>DBPROP_NOTIFYROWUPDATE</p></td>
</tr>
<tr class="even">
<td><p>Rowset Fetch Position Change Notification</p></td>
<td><p>DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE</p></td>
</tr>
<tr class="odd">
<td><p>Rowset Release Notification</p></td>
<td><p>DBPROP_NOTIFYROWSETRELEASE</p></td>
</tr>
<tr class="even">
<td><p>Scroll Backwards</p></td>
<td><p>DBPROP_CANSCROLLBACKWARDS</p></td>
</tr>
<tr class="odd">
<td><p>Server Cursor</p></td>
<td><p>DBPROP_SERVERCURSOR</p></td>
</tr>
<tr class="even">
<td><p>Server Data on Insert</p></td>
<td><p>DBPROP_SERVERDATAONINSERT</p></td>
</tr>
<tr class="odd">
<td><p>Skip Deleted Bookmarks</p></td>
<td><p>DBPROP_BOOKMARKSKIP</p></td>
</tr>
<tr class="even">
<td><p>Strong Row Identity</p></td>
<td><p>DBPROP_STRONGIDENTITY</p></td>
</tr>
<tr class="odd">
<td><p>Updatability</p></td>
<td><p>DBPROP_UPDATABILITY</p></td>
</tr>
<tr class="even">
<td><p>Use Bookmarks</p></td>
<td><p>DBPROP_BOOKMARKS</p></td>
</tr>
<tr class="odd">
<td><p>XML Root</p></td>
<td><p>SSPROP_STREAM_XMLROOT</p></td>
</tr>
<tr class="even">
<td><p>XSL</p></td>
<td><p>SSPROP_STREAM_XSL</p></td>
</tr>
</tbody>
</table>


For specific implementation details and functional information about the Microsoft SQL Server OLE DB Provider, consult the OLE DB Provider for SQL Server documentation in the OLE DB section of the MDAC SDK.

