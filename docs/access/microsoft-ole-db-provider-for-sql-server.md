---
title: "Microsoft OLE DB Provider for SQL Server"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 0ffdea03-1a76-499b-f649-423f6b3c13d7
description: "The Microsoft OLE DB Provider for SQL Server, SQLOLEDB, allows ADO to access Microsoft SQL Server."
---

# Microsoft OLE DB Provider for SQL Server

The Microsoft OLE DB Provider for SQL Server, SQLOLEDB, allows ADO to access Microsoft SQL Server.
  
## Connection String Parameters

To connect to this provider, set the  *Provider*  argument to the [ConnectionString](connectionstring-property-ado.md) property to: 
  
```
 
SQLOLEDB 

```

This value can also be set or read using the [Provider](provider-property-ado.md) property. 
  
## Typical Connection String

A typical connection string for this provider is:
  
```
 
"Provider=SQLOLEDB;Data Source=serverName ;" 
Initial Catalog=databaseName ; 
User ID=userName ;Password=userPassword ;" 

```

The string consists of these keywords:
  
|**Keyword**|**Description**|
|:-----|:-----|
|**Provider** <br/> |Specifies the OLE DB Provider for SQL Server.  <br/> |
|**Data Source** or **Server** <br/> |Specifies the name of a server.  <br/> |
|**Initial Catalog** or **Database** <br/> |Specifies the name of a database on the server.  <br/> |
|**User ID** or **uid** <br/> |Specifies the user name (for SQL Server Authentication).  <br/> |
|**Password** or **pwd** <br/> |Specifies the user password (for SQL Server Authentication).  <br/> |
   
## Provider-Specific Connection Parameters

The provider supports several provider-specific connection parameters in addition to those defined by ADO. As with the ADO connection properties, these provider-specific properties can be set via the [Properties](properties-collection-ado.md) collection of a [Connection](connection-object-ado.md) or can be set as part of the **ConnectionString**. 
  
|**Parameter**|**Description**|
|:-----|:-----|
|Trusted_Connection  <br/> |Indicates the user authentication mode. This can be set to **Yes** or **No**. The default value is **No**. If this property is set to **Yes**, then SQLOLEDB uses Microsoft Windows NT Authentication Mode to authorize user access to the SQL Server database specified by the **Location** and [Datasource](datasource-property-ado.md) property values. If this property is set to **No**, then SQLOLEDB uses Mixed Mode to authorize user access to the SQL Server database. The SQL Server login and password are specified in the **User Id** and **Password** properties.  <br/> |
|Current Language  <br/> |Indicates a SQL Server language name. Identifies the language used for system message selection and formatting. The language must be installed on the SQL Server, otherwise opening the connection will fail.  <br/> |
|Network Address  <br/> |Indicates the network address of the SQL Server specified by the **Location** property.  <br/> |
|Network Library  <br/> |Indicates the name of the network library (dynamic-link libraries) used to communicate with the SQL Server. The name should not include the path or the .dll file name extension. The default is provided by the SQL Server client configuration.  <br/> |
|Use Procedure for Prepare  <br/> |Determines whether SQL Server creates temporary stored procedures when Commands are prepared (by the **Prepared** property).  <br/> |
|Auto Translate  <br/> |Indicates whether OEM/ANSI characters are converted. This property can be set to **True** or **False**. The default value is **True**. If this property is set to **True**, then SQLOLEDB performs OEM/ANSI character conversion when multi-byte character strings are retrieved from, or sent to, the SQL Server. If this property is set to **False**, then SQLOLEDB does not perform OEM/ANSI character conversion on multi-byte character string data.  <br/> |
|Packet Size  <br/> |Indicates a network packet size in bytes. The packet size property value must be between 512 and 32767. The default SQLOLEDB network packet size is 4096.  <br/> |
|Application Name  <br/> |Indicates the client application name.  <br/> |
|Workstation ID  <br/> |A string identifying the workstation.  <br/> |
   
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
  
|**ADO Property Name**|**OLE DB Property Name**|
|:-----|:-----|
|Active Sessions  <br/> |DBPROP_ACTIVESESSIONS  <br/> |
|Asynchable Abort  <br/> |DBPROP_ASYNCTXNABORT  <br/> |
|Asynchable Commit  <br/> |DBPROP_ASYNCTNXCOMMIT  <br/> |
|Autocommit Isolation Levels  <br/> |DBPROP_SESS_AUTOCOMMITISOLEVELS  <br/> |
|Catalog Location  <br/> |DBPROP_CATALOGLOCATION  <br/> |
|Catalog Term  <br/> |DBPROP_CATALOGTERM  <br/> |
|Column Definition  <br/> |DBPROP_COLUMNDEFINITION  <br/> |
|Connect Timeout  <br/> |DBPROP_INIT_TIMEOUT  <br/> |
|Current Catalog  <br/> |DBPROP_CURRENTCATALOG  <br/> |
|Data Source  <br/> |DBPROP_INIT_DATASOURCE  <br/> |
|Data Source Name  <br/> |DBPROP_DATASOURCENAME  <br/> |
|Data Source Object Threading Model  <br/> |DBPROP_DSOTHREADMODEL  <br/> |
|DBMS Name  <br/> |DBPROP_DBMSNAME  <br/> |
|DBMS Version  <br/> |DBPROP_DBMSVER  <br/> |
|Extended Properties  <br/> |DBPROP_INIT_PROVIDERSTRING  <br/> |
|GROUP BY Support  <br/> |DBPROP_GROUPBY  <br/> |
|Heterogeneous Table Support  <br/> |DBPROP_HETEROGENEOUSTABLES  <br/> |
|Identifier Case Sensitivity  <br/> |DBPROP_IDENTIFIERCASE  <br/> |
|Initial Catalog  <br/> |DBPROP_INIT_CATALOG  <br/> |
|Isolation Levels  <br/> |DBPROP_SUPPORTEDTXNISOLEVELS  <br/> |
|Isolation Retention  <br/> |DBPROP_SUPPORTEDTXNISORETAIN  <br/> |
|Locale Identifier  <br/> |DBPROP_INIT_LCID  <br/> |
|Maximum Index Size  <br/> |DBPROP_MAXINDEXSIZE  <br/> |
|Maximum Row Size  <br/> |DBPROP_MAXROWSIZE  <br/> |
|Maximum Row Size Includes BLOB  <br/> |DBPROP_MAXROWSIZEINCLUDESBLOB  <br/> |
|Maximum Tables in SELECT  <br/> |DBPROP_MAXTABLESINSELECT  <br/> |
|Multiple Parameter Sets  <br/> |DBPROP_MULTIPLEPARAMSETS  <br/> |
|Multiple Results  <br/> |DBPROP_MULTIPLERESULTS  <br/> |
|Multiple Storage Objects  <br/> |DBPROP_MULTIPLESTORAGEOBJECTS  <br/> |
|Multi-Table Update  <br/> |DBPROP_MULTITABLEUPDATE  <br/> |
|NULL Collation Order  <br/> |DBPROP_NULLCOLLATION  <br/> |
|NULL Concatenation Behavior  <br/> |DBPROP_CONCATNULLBEHAVIOR  <br/> |
|OLE DB Version  <br/> |DBPROP_PROVIDEROLEDBVER  <br/> |
|OLE Object Support  <br/> |DBPROP_OLEOBJECTS  <br/> |
|Open Rowset Support  <br/> |DBPROP_OPENROWSETSUPPORT  <br/> |
|ORDER BY Columns in Select List  <br/> |DBPROP_ORDERBYCOLUMNSINSELECT  <br/> |
|Output Parameter Availability  <br/> |DBPROP_OUTPUTPARAMETERAVAILABILITY  <br/> |
|Pass By Ref Accessors  <br/> |DBPROP_BYREFACCESSORS  <br/> |
|Password  <br/> |DBPROP_AUTH_PASSWORD  <br/> |
|Persist Security Info  <br/> |DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO  <br/> |
|Persistent ID Type  <br/> |DBPROP_PERSISTENTIDTYPE  <br/> |
|Prepare Abort Behavior  <br/> |DBPROP_PREPAREABORTBEHAVIOR  <br/> |
|Prepare Commit Behavior  <br/> |DBPROP_PREPARECOMMITBEHAVIOR  <br/> |
|Procedure Term  <br/> |DBPROP_PROCEDURETERM  <br/> |
|Prompt  <br/> |DBPROP_INIT_PROMPT  <br/> |
|Provider Friendly Name  <br/> |DBPROP_PROVIDERFRIENDLYNAME  <br/> |
|Provider Name  <br/> |DBPROP_PROVIDERFILENAME  <br/> |
|Provider Version  <br/> |DBPROP_PROVIDERVER  <br/> |
|Read-Only Data Source  <br/> |DBPROP_DATASOURCEREADONLY  <br/> |
|Rowset Conversions on Command  <br/> |DBPROP_ROWSETCONVERSIONSONCOMMAND  <br/> |
|Schema Term  <br/> |DBPROP_SCHEMATERM  <br/> |
|Schema Usage  <br/> |DBPROP_SCHEMAUSAGE  <br/> |
|SQL Support  <br/> |DBPROP_SQLSUPPORT  <br/> |
|Structured Storage  <br/> |DBPROP_STRUCTUREDSTORAGE  <br/> |
|Subquery Support  <br/> |DBPROP_SUBQUERIES  <br/> |
|Table Term  <br/> |DBPROP_TABLETERM  <br/> |
|Transaction DDL  <br/> |DBPROP_SUPPORTEDTXNDDL  <br/> |
|User ID  <br/> |DBPROP_AUTH_USERID  <br/> |
|User Name  <br/> |DBPROP_USERNAME  <br/> |
|Window Handle  <br/> |DBPROP_INIT_HWND  <br/> |
   
## Recordset Dynamic Properties

The following properties are added to the **Recordset** object's **Properties** collection. 
  
|**ADO Property Name**|**OLE DB Property Name**|
|:-----|:-----|
|Access Order  <br/> |DBPROP_ACCESSORDER  <br/> |
|Blocking Storage Objects  <br/> |DBPROP_BLOCKINGSTORAGEOBJECTS  <br/> |
|Bookmark Type  <br/> |DBPROP_BOOKMARKTYPE  <br/> |
|Bookmarkable  <br/> |DBPROP_IROWSETLOCATE  <br/> |
|Change Inserted Rows  <br/> |DBPROP_CHANGEINSERTEDROWS  <br/> |
|Column Privileges  <br/> |DBPROP_COLUMNRESTRICT  <br/> |
|Column Set Notification  <br/> |DBPROP_NOTIFYCOLUMNSET  <br/> |
|Command Time Out  <br/> |DBPROP_COMMANDTIMEOUT  <br/> |
|Defer Column  <br/> |DBPROP_DEFERRED  <br/> |
|Delay Storage Object Updates  <br/> |DBPROP_DELAYSTORAGEOBJECTS  <br/> |
|Fetch Backwards  <br/> |DBPROP_CANFETCHBACKWARDS  <br/> |
|Hold Rows  <br/> |DBPROP_CANHOLDROWS  <br/> |
|IAccessor  <br/> |DBPROP_IAccessor  <br/> |
|IColumnsInfo  <br/> |DBPROP_IColumnsInfo  <br/> |
|IColumnsRowset  <br/> |DBPROP_IColumnsRowset  <br/> |
|IConnectionPointContainer  <br/> |DBPROP_IConnectionPointContainer  <br/> |
|IConvertType  <br/> |DBPROP_IConvertType  <br/> |
|Immobile Rows  <br/> |DBPROP_IMMOBILEROWS  <br/> |
|IRowset  <br/> |DBPROP_IRowset  <br/> |
|IRowsetChange  <br/> |DBPROP_IRowsetChange  <br/> |
|IRowsetIdentity  <br/> |DBPROP_IRowsetIdentity  <br/> |
|IRowsetInfo  <br/> |DBPROP_IRowsetInfo  <br/> |
|IRowsetLocate  <br/> |DBPROP_IRowsestLocate  <br/> |
|IRowsetResynch  <br/> ||
|IRowsetScroll  <br/> |DBPROP_IRowsetScroll  <br/> |
|IRowsetUpdate  <br/> |DBPROP_IRowsetUpdate  <br/> |
|ISequentialStream  <br/> |DBPROP_ISequentialStream  <br/> |
|ISupportErrorInfo  <br/> |DBPROP_ISupportErrorInfo  <br/> |
|Literal Bookmarks  <br/> |DBPROP_LITERALBOOKMARKS  <br/> |
|Literal Row Identity  <br/> |DBPROP_LITERALIDENTITY  <br/> |
|Maximum Open Rows  <br/> |DBPROP_MAXOPENROWS  <br/> |
|Maximum Pending Rows  <br/> |DBPROP_MAXPENDINGROWS  <br/> |
|Maximum Rows  <br/> |DBPROP_MAXROWS  <br/> |
|Notification Granularity  <br/> |DBPROP_NOTIFICATIONGRANULARITY  <br/> |
|Notification Phases  <br/> |DBPROP_NOTIFICATIONPHASES  <br/> |
|Objects Transacted  <br/> |DBPROP_TRANSACTEDOBJECT  <br/> |
|Others' Changes Visible  <br/> |DBPROP_OTHERUPDATEDELETE  <br/> |
|Others' Inserts Visible  <br/> |DBPROP_OTHERINSERT  <br/> |
|Own Changes Visible  <br/> |DBPROP_OWNUPDATEDELETE  <br/> |
|Own Inserts Visible  <br/> |DBPROP_OWNINSERT  <br/> |
|Preserve on Abort  <br/> |DBPROP_ABORTPRESERVE  <br/> |
|Preserve on Commit  <br/> |DBPROP_COMMITPRESERVE  <br/> |
|Quick Restart  <br/> |DBPROP_QUICKRESTART  <br/> |
|Reentrant Events  <br/> |DBPROP_REENTRANTEVENTS  <br/> |
|Remove Deleted Rows  <br/> |DBPROP_REMOVEDELETED  <br/> |
|Report Multiple Changes  <br/> |DBPROP_REPORTMULTIPLECHANGES  <br/> |
|Return Pending Inserts  <br/> |DBPROP_RETURNPENDINGINSERTS  <br/> |
|Row Delete Notification  <br/> |DBPROP_NOTIFYROWDELETE  <br/> |
|Row First Change Notification  <br/> |DBPROP_NOTIFYROWFIRSTCHANGE  <br/> |
|Row Insert Notification  <br/> |DBPROP_NOTIFYROWINSERT  <br/> |
|Row Privileges  <br/> |DBPROP_ROWRESTRICT  <br/> |
|Row Resynchronization Notification  <br/> |DBPROP_NOTIFYROWRESYNCH  <br/> |
|Row Threading Model  <br/> |DBPROP_ROWTHREADMODEL  <br/> |
|Row Undo Change Notification  <br/> |DBPROP_NOTIFYROWUNDOCHANGE  <br/> |
|Row Undo Delete Notification  <br/> |DBPROP_NOTIFYROWUNDODELETE  <br/> |
|Row Undo Insert Notification  <br/> |DBPROP_NOTIFYROWUNDOINSERT  <br/> |
|Row Update Notification  <br/> |DBPROP_NOTIFYROWUPDATE  <br/> |
|Rowset Fetch Position Change Notification  <br/> |DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE  <br/> |
|Rowset Release Notification  <br/> |DBPROP_NOTIFYROWSETRELEASE  <br/> |
|Scroll Backwards  <br/> |DBPROP_CANSCROLLBACKWARDS  <br/> |
|Server Cursor  <br/> |DBPROP_SERVERCURSOR  <br/> |
|Skip Deleted Bookmarks  <br/> |DBPROP_BOOKMARKSKIPPED  <br/> |
|Strong Row Identity  <br/> |DBPROP_STRONGITDENTITY  <br/> |
|Unique Rows  <br/> |DBPROP_UNIQUEROWS  <br/> |
|Updatability  <br/> |DBPROP_UPDATABILITY  <br/> |
|Use Bookmarks  <br/> |DBPROP_BOOKMARKS  <br/> |
   
## Command Dynamic Properties

The following properties are added to the **Command** object's **Properties** collection. 
  
|**ADO Property Name**|**OLE DB Property Name**|
|:-----|:-----|
|Access Order  <br/> |DBPROP_ACCESSORDER  <br/> |
|Base Path  <br/> |SSPROP_STREAM_BASEPATH  <br/> |
|Blocking Storage Objects  <br/> |DBPROP_BLOCKINGSTORAGEOBJECTS  <br/> |
|Bookmark Type  <br/> |DBPROP_BOOKMARKTYPE  <br/> |
|Bookmarkable  <br/> |DBPROP_IROWSETLOCATE  <br/> |
|Change Inserted Rows  <br/> |DBPROP_CHANGEINSERTEDROWS  <br/> |
|Column Privileges  <br/> |DBPROP_COLUMNRESTRICT  <br/> |
|Column Set Notification  <br/> |DBPROP_NOTIFYCOLUMNSET  <br/> |
|Content Type  <br/> |SSPROP_STREAM_CONTENTTYPE  <br/> |
|Cursor Auto Fetch  <br/> |SSPROP_CURSORAUTOFETCH  <br/> |
|Defer Column  <br/> |DBPROP_DEFERRED  <br/> |
|Defer Prepare  <br/> |SSPROP_DEFERPREPARE  <br/> |
|Delay Storage Object Updates  <br/> |DBPROP_DELAYSTORAGEOBJECTS  <br/> |
|Fetch Backwards  <br/> |DBPROP_CANFETCHBACKWARDS  <br/> |
|Hold Rows  <br/> |DBPROP_CANHOLDROWS  <br/> |
|IAccessor  <br/> |DBPROP_IAccessor  <br/> |
|IColumnsInfo  <br/> |DBPROP_IColumnsInfo  <br/> |
|IColumnsRowset  <br/> |DBPROP_IColumnsRowset  <br/> |
|IConnectionPointContainer  <br/> |DBPROP_IConnectionPointContainer  <br/> |
|IConvertType  <br/> |DBPROP_IConvertType  <br/> |
|Immobile Rows  <br/> |DBPROP_IMMOBILEROWS  <br/> |
|IRowset  <br/> |DBPROP_IRowset  <br/> |
|IRowsetChange  <br/> |DBPROP_IRowsetChange  <br/> |
|IRowsetIdentity  <br/> |DBPROP_IRowsetIdentity  <br/> |
|IRowsetInfo  <br/> |DBPROP_IRowsetInfo  <br/> |
|IRowsetLocate  <br/> |DBPROP_IRowsetLocate  <br/> |
|IRowsetResynch  <br/> |DBPROP_IRowsetResynch  <br/> |
|IRowsetScroll  <br/> |DBPROP_IRowsetScroll  <br/> |
|IRowsetUpdate  <br/> |DBPROP_IRowsetUpdate  <br/> |
|ISequentialStream  <br/> |DBPROP_ISequentialStream  <br/> |
|ISupportErrorInfo  <br/> |DBPROP_ISupportErrorInfo  <br/> |
|Literal Bookmarks  <br/> |DBPROP_LITERALBOOKMARKS  <br/> |
|Literal Row Identity  <br/> |DBPROP_LITERALIDENTITY  <br/> |
|Lock Mode  <br/> |DBPROP_LOCKMODE  <br/> |
|Maximum Open Rows  <br/> |DBPROP_MAXOPENROWS  <br/> |
|Maximum Pending Rows  <br/> |DBPROP_MAXPENDINGROWS  <br/> |
|Maximum Rows  <br/> |DBPROP_MAXROWS  <br/> |
|Notification Granularity  <br/> |DBPROP_NOTIFICATIONGRANULARITY  <br/> |
|Notification Phases  <br/> |DBPROP_NOTIFICATIONPHASES  <br/> |
|Objects Transacted  <br/> |DBPROP_TRANSACTEDOBJECT  <br/> |
|Others' Changes Visible  <br/> |DBPROP_OTHERUPDATEDELETE  <br/> |
|Others' Inserts Visible  <br/> |DBPROP_OTHERINSERT  <br/> |
|Output Encoding Property  <br/> |DBPROP_OUTPUTENCODING  <br/> |
|Output Stream Property  <br/> |DBPROP_OUTPUTSTREAM  <br/> |
|Own Changes Visible  <br/> |DBPROP_OWNUPDATEDELETE  <br/> |
|Own Inserts Visible  <br/> |DBPROP_OWNINSERT  <br/> |
|Preserve on Abort  <br/> |DBPROP_ABORTPRESERVE  <br/> |
|Preserve on Commit  <br/> |DBPROP_COMMITPRESERVE  <br/> |
|Quick Restart  <br/> |DBPROP_QUICKRESTART  <br/> |
|Reentrant Events  <br/> |DBPROP_REENTRANTEVENTS  <br/> |
|Remove Deleted Rows  <br/> |DBPROP_REMOVEDELETED  <br/> |
|Report Multiple Changes  <br/> |DBPROP_REPORTMULTIPLECHANGES  <br/> |
|Return Pending Inserts  <br/> |DBPROP_RETURNPENDINGINSERTS  <br/> |
|Row Delete Notification  <br/> |DBPROP_NOTIFYROWDELETE  <br/> |
|Row First Change Notification  <br/> |DBPROP_NOTIFYROWFIRSTCHANGE  <br/> |
|Row Insert Notification  <br/> |DBPROP_NOTIFYROWINSERT  <br/> |
|Row Privileges  <br/> |DBPROP_ROWRESTRICT  <br/> |
|Row Resynchronization Notification  <br/> |DBPROP_NOTIFYROWRESYNCH  <br/> |
|Row Threading Model  <br/> |DBPROP_ROWTHREADMODEL  <br/> |
|Row Undo Change Notification  <br/> |DBPROP_NOTIFYROWUNDOCHANGE  <br/> |
|Row Undo Delete Notification  <br/> |DBPROP_NOTIFYROWUNDODELETE  <br/> |
|Row Undo Insert Notification  <br/> |DBPROP_NOTIFYROWUNDOINSERT  <br/> |
|Row Update Notification  <br/> |DBPROP_NOTIFYROWUPDATE  <br/> |
|Rowset Fetch Position Change Notification  <br/> |DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE  <br/> |
|Rowset Release Notification  <br/> |DBPROP_NOTIFYROWSETRELEASE  <br/> |
|Scroll Backwards  <br/> |DBPROP_CANSCROLLBACKWARDS  <br/> |
|Server Cursor  <br/> |DBPROP_SERVERCURSOR  <br/> |
|Server Data on Insert  <br/> |DBPROP_SERVERDATAONINSERT  <br/> |
|Skip Deleted Bookmarks  <br/> |DBPROP_BOOKMARKSKIP  <br/> |
|Strong Row Identity  <br/> |DBPROP_STRONGIDENTITY  <br/> |
|Updatability  <br/> |DBPROP_UPDATABILITY  <br/> |
|Use Bookmarks  <br/> |DBPROP_BOOKMARKS  <br/> |
|XML Root  <br/> |SSPROP_STREAM_XMLROOT  <br/> |
|XSL  <br/> |SSPROP_STREAM_XSL  <br/> |
   
For specific implementation details and functional information about the Microsoft SQL Server OLE DB Provider, consult the OLE DB Provider for SQL Server documentation in the OLE DB section of the MDAC SDK.
  

