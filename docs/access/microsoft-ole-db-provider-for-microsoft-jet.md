---
title: "Microsoft OLE DB Provider for Microsoft Jet"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 4a210d72-8c90-aa7c-4621-1a555a30a2d2

description: "The OLE DB Provider for Microsoft Jet allows ADO to access Microsoft Jet databases."
---

# Microsoft OLE DB Provider for Microsoft Jet

The OLE DB Provider for Microsoft Jet allows ADO to access Microsoft Jet databases.
  
## Connection String Parameters

To connect to this provider, set the  *Provider*  argument of the [ConnectionString](connectionstring-property-ado.md) property to: 
  
```
 
Microsoft.Jet.OLEDB.4.0 

```

Reading the [Provider](provider-property-ado.md) property will return this string as well. 
  
## Typical Connection String

A typical connection string for this provider is:
  
```
 
"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=databaseName ;User ID=userName ;Password=userPassword ;" 

```

The string consists of these keywords:
  
|**Keyword**|**Description**|
|:-----|:-----|
|**Provider** <br/> |Specifies the OLE DB Provider for Microsoft Jet.  <br/> |
|**Data Source** <br/> |Specifies the database path and file name (for example,  `c:\Northwind.mdb`).  <br/> |
|**User ID** <br/> |Specifies the user name. If this keyword is not specified, the string, " `admin`", is used by default.  <br/> |
|**Password** <br/> |Specifies the user password. If this keyword is not specified, the empty string (""), is used by default.  <br/> |
   
## Provider-Specific Connection Parameters

The OLE DB Provider for Microsoft Jet supports several provider-specific dynamic properties in addition to those defined by ADO. As with all other **Connection** parameters, they can be set via the **Connection** object's **Properties** collection or as part of the connection string. 
  
The following table lists these properties with the corresponding OLE DB property name in parentheses.
  
|**Parameter**|**Description**|
|:-----|:-----|
|Jet OLEDB:Compact Reclaimed Space Amount           (DBPROP_JETOLEDB_COMPACTFREESPACESIZE)  <br/> |Indicates an estimate of the amount of space, in bytes, that can be reclaimed by compacting the database. This value is only valid after a database connection has been established.  <br/> |
|Jet OLEDB:Connection Control           (DBPROP_JETOLEDB_CONNECTIONCONTROL)  <br/> |Indicates whether users can connect to the database.  <br/> |
|Jet OLEDB:Create System Database           (DBPROP_JETOLEDB_CREATESYSTEMDATABASE)  <br/> |Indicates whether a system database should be created when creating a new data source.  <br/> |
|Jet OLEDB:Database Locking Mode           (DBPROP_JETOLEDB_DATABASELOCKMODE)  <br/> |Indicates the locking mode for this database. The first user to open the database determines the mode used while the database is open.  <br/> |
|Jet OLEDB:Database Password           (DBPROP_JETOLEDB_DATABASEPASSWORD)  <br/> |Indicates the database password.  <br/> |
|Jet OLEDB:Don't Copy Locale on Compact           (DBPROP_JETOLEDB_COMPACT_DONTCOPYLOCALE)  <br/> |Indicates whether Jet should copy locale information when compacting a database.  <br/> |
|Jet OLEDB:Encrypt Database           (DBPROP_JETOLEDB_ENCRYPTDATABASE)  <br/> |Indicates whether a compacted database should be encrypted. If this property is not set, the compacted database will be encrypted if the original database was also encrypted.  <br/> |
|Jet OLEDB:Engine Type           (DBPROP_JETOLEDB_ENGINE)  <br/> |Indicates the storage engine used to access the current data store.  <br/> |
|Jet OLEDB:Exclusive Async Delay           (DBPROP_JETOLEDB_EXCLUSIVEASYNCDELAY)  <br/> |Indicates the maximum length of time, in milliseconds, that Jet can delay asynchronous writes to disk when the database is opened exclusively. This property is ignored unless **Jet OLEDB:Flush Transaction Timeout** is set to 0.  <br/> |
|Jet OLEDB:Flush Transaction Timeout           (DBPROP_JETOLEDB_FLUSHTRANSACTIONTIMEOUT)  <br/> |Indicates the amount of time to wait before data stored in a cache for asynchronous writing is actually written to disk. This setting overrides the values for **Jet OLEDB:Shared Async Delay** and **Jet OLEDB:Exclusive Async Delay**.  <br/> |
|Jet OLEDB:Global Bulk Transactions           (DBPROP_JETOLEDB_GLOBALBULKNOTRANSACTIONS)  <br/> |Indicates whether SQL bulk transactions are transacted.  <br/> |
|Jet OLEDB:Global Partial Bulk Ops           (DBPROP_JETOLEDB_GLOBALBULKPARTIAL)  <br/> |Indicates the password used to open the database.  <br/> |
|Jet OLEDB:Implicit Commit Sync           (DBPROP_JETOLEDB_IMPLICITCOMMITSYNC)  <br/> |Indicates whether changes made in internal implicit transactions are written in synchronous or asynchronous mode.  <br/> |
|Jet OLEDB:Lock Delay           (DBPROP_JETOLEDB_LOCKDELAY)  <br/> |Indicates the number of milliseconds to wait before attempting to acquire a lock after a previous attempt has failed.  <br/> |
|Jet OLEDB:Lock Retry           (DBPROP_JETOLEDB_LOCKRETRY)  <br/> |Indicates how many times an attempt to access a locked page is repeated.  <br/> |
|Jet OLEDB:Max Buffer Size           (DBPROP_JETOLEDB_MAXBUFFERSIZE)  <br/> |Indicates the maximum amount of memory, in kilobytes, Jet can use before it starts flushing changes to disk.  <br/> |
|Jet OLEDB:Max Locks Per File           (DBPROP_JETOLEDB_MAXLOCKSPERFILE)  <br/> |Indicates the maximum number of locks Jet can place on a database. The default value is 9500.  <br/> |
|Jet OLEDB:New Database Password           (DBPROP_JETOLEDB_NEWDATABASEPASSWORD)  <br/> |Indicates the new password to be set for this database. The old password is stored in **Jet OLEDB:Database Password**.  <br/> |
|Jet OLEDB:ODBC Command Time Out           (DBPROP_JETOLEDB_ODBCCOMMANDTIMEOUT)  <br/> |Indicates the number of milliseconds before a remote ODBC query from Jet will timeout.  <br/> |
|Jet OLEDB:Page Locks to Table Lock           (DBPROP_JETOLEDB_PAGELOCKSTOTABLELOCK)  <br/> |Indicates how many pages need to be locked within a transaction before Jet attempts to promote the lock to a table lock. If this value is 0, then the lock is never promoted.  <br/> |
|Jet OLEDB:Page Timeout           (DBPROP_JETOLEDB_PAGETIMEOUT)  <br/> |Indicates the number of milliseconds Jet will wait before checking to see if its cache is out of date with the database file.  <br/> |
|Jet OLEDB:Recycle Long-Valued Pages           (DBPROP_JETOLEDB_RECYCLELONGVALUEPAGES)  <br/> |Indicates whether Jet should aggressively try to reclaim BLOB pages when they are freed.  <br/> |
|Jet OLEDB:Registry Path           (DBPROP_JETOLEDB_REGPATH)  <br/> |Indicates the Windows registry key that contains values for the Jet database engine.  <br/> |
|Jet OLEDB:Reset ISAM Stats           (DBPROP_JETOLEDB_RESETISAMSTATS)  <br/> |Indicates whether the schema **Recordset** DBSCHEMA_JETOLEDB_ISAMSTATS should reset its performance counters after returning performance information.  <br/> |
|Jet OLEDB:Shared Async Delay           (DBPROP_JETOLEDB_SHAREDASYNCDELAY)  <br/> |Indicates the maximum amount of time, in milliseconds, Jet can delay asynchronous writes to disk when the database is opened in multi-user mode.  <br/> |
|Jet OLEDB:System Database           (DBPROP_JETOLEDB_SYSDBPATH)  <br/> |Indicates the path and file name for the workgroup information file (system database).  <br/> |
|Jet OLEDB:Transaction Commit Mode           (DBPROP_JETOLEDB_TXNCOMMITMODE)  <br/> |Indicates whether Jet writes data to disk synchronously or asynchronously when a transaction is committed.  <br/> |
|Jet OLEDB:User Commit Sync           (DBPROP_JETOLEDB_USERCOMMITSYNC)  <br/> |Indicates whether changes made in transactions are written in synchronous or asynchronous mode.  <br/> |
   
## Provider-Specific Recordset and Command Properties

The Jet provider also supports several provider-specific **Recordset** and **Command** properties. These properties are accessed and set through the **Properties** collection of the **Recordset** or **Command** object. The table lists the ADO property name and its corresponding OLE DB property name in parentheses. 
  
|**Property Name**|**Description**|
|:-----|:-----|
|Jet OLEDB:Bulk Transactions           (DBPROP_JETOLEDB_BULKNOTRANSACTIONS)  <br/> |Indicates whether SQL bulk operations are transacted. Large bulk operations might fail when transacted, due to resource delays.  <br/> |
|Jet OLEDB:Enable Fat Cursors           (DBPROP_JETOLEDB_ENABLEFATCURSOR)  <br/> |Indicates whether Jet should cache multiple rows when populating a recordset for remote row sources.  <br/> |
|Jet OLEDB:Fat Cursor Cache Size           (DBPROP_JETOLEDB_FATCURSORMAXROWS)  <br/> |Indicates the number of rows to cache when using remote data store row caching. This value is ignored unless **Jet OLEDB:Enable Fat Cursors** is True.  <br/> |
|Jet OLEDB:Inconsistent           (DBPROP_JETOLEDB_INCONSISTENT)  <br/> |Indicates whether query results allow inconsistent updates.  <br/> |
|Jet OLEDB:Locking Granularity           (DBPROP_JETOLEDB_LOCKGRANULARITY)  <br/> |Indicates whether a table is opened using row-level locking.  <br/> |
|Jet OLEDB:ODBC Pass-Through Statement           (DBPROP_JETOLEDB_ODBCPASSTHROUGH)  <br/> |Indicates that Jet should pass the SQL text in a **Command** object to the back end unaltered.  <br/> |
|Jet OLEDB:Partial Bulk Ops           (DBPROP_JETOLEDB_BULKPARTIAL)  <br/> |Indicates Jet's behavior when SQL DML operations fail.  <br/> |
|Jet OLEDB:Pass Through Query Bulk-Op           (DBPROP_JETOLEDB_PASSTHROUGHBULKOP)  <br/> |Indicates whether queries that do not return a **Recordset** are passed unaltered to the data source.  <br/> |
|Jet OLEDB:Pass Through Query Connect String           (DBPROP_JETOLEDB_ODBCPASSTHROUGHCONNECTSTRING)  <br/> |Indicates the Jet connect string used to connect to a remote data store. This value is ignored unless **Jet OLEDB:ODBC Pass-Through Statement** is True.  <br/> |
|Jet OLEDB:Stored Query           (DBPROP_JETOLEDB_STOREDQUERY)  <br/> |Indicates whether the command text should be interpreted as a stored query instead of an SQL command.  <br/> |
|Jet OLEDB:Validate Rules On Set           (DBPROP_JETOLEDB_VALIDATEONSET)  <br/> |Indicates whether the Jet validation rules are evaluated when column data is set or when the changes are committed to the database.  <br/> |
   
By default, the OLE DB Provider for Microsoft Jet opens Microsoft Jet databases in read/write mode. To open a database in read-only mode, set the [Mode](mode-property-ado.md) property on the ADO **Connection** object to **adModeRead**. 
  
## Command Object Usage

Command text in the [Command](command-object-ado.md) object uses the Microsoft Jet SQL dialect. You can specify row-returning queries, action queries, and table names in the command text; however, stored procedures are not supported and should not be specified. 
  
## Recordset Behavior

The Microsoft Jet database engine does not support dynamic cursors. Therefore, the OLE DB Provider for Microsoft Jet does not support the **adLockDynamic** cursor type. When a dynamic cursor is requested, the provider will return a keyset cursor and reset the [CursorType](cursortype-property-ado.md) property to indicate the type of [Recordset](recordset-object-ado.md) returned. Further, if an updatable **Recordset** is requested ( **LockType** is **adLockOptimistic**, **adLockBatchOptimistic**, or **adLockPessimistic** ) the provider will also return a keyset cursor and reset the **CursorType** property. 
  
## Dynamic Properties

The OLE DB Provider for Microsoft Jet inserts several dynamic properties into the **Properties** collection of the unopened [Connection](connection-object-ado.md), [Recordset](recordset-object-ado.md), and [Command](command-object-ado.md) objects. 
  
The tables below are a cross-index of the ADO and OLE DB names for each dynamic property. The OLE DB Programmer's Reference refers to an ADO property name by the term, "Description." You can find more information about these properties in the OLE DB Programmer's Reference. Search for the OLE DB property name in the Index or see Appendix C: OLE DB Properties.
  
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
|Current Catalog  <br/> |DBPROP_CURRENTCATALOG  <br/> |
|Data Source  <br/> |DBPROP_INIT_DATASOURCE  <br/> |
|Data Source Name  <br/> |DBPROP_DATASOURCENAME  <br/> |
|Data Source Object Threading Model  <br/> |DBPROP_DSOTHREADMODEL  <br/> |
|DBMS Name  <br/> |DBPROP_DBMSNAME  <br/> |
|DBMS Version  <br/> |DBPROP_DBMSVER  <br/> |
|GROUP BY Support  <br/> |DBPROP_GROUPBY  <br/> |
|Heterogeneous Table Support  <br/> |DBPROP_HETEROGENEOUSTABLES  <br/> |
|Identifier Case Sensitivity  <br/> |DBPROP_IDENTIFIERCASE  <br/> |
|Isolation Levels  <br/> |DBPROP_SUPPORTEDTXNISOLEVELS  <br/> |
|Isolation Retention  <br/> |DBPROP_SUPPORTEDTXNISORETAIN  <br/> |
|Locale Identifier  <br/> |DBPROP_INIT_LCID  <br/> |
|Maximum Index Size  <br/> |DBPROP_MAXINDEXSIZE  <br/> |
|Maximum Row Size  <br/> |DBPROP_MAXROWSIZE  <br/> |
|Maximum Row Size Includes BLOB  <br/> |DBPROP_MAXROWSIZEINCLUDESBLOB  <br/> |
|Maximum Tables in SELECT  <br/> |DBPROP_MAXTABLESINSELECT  <br/> |
|Mode  <br/> |DBPROP_INIT_MODE  <br/> |
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
|Append-Only Rowset  <br/> |DBPROP_APPENDONLY  <br/> |
|Blocking Storage Objects  <br/> |DBPROP_BLOCKINGSTORAGEOBJECTS  <br/> |
|Bookmark Type  <br/> |DBPROP_BOOKMARKTYPE  <br/> |
|Bookmarkable  <br/> |DBPROP_IROWSETLOCATE  <br/> |
|Bookmarks Ordered  <br/> |DBPROP_ORDEREDBOOKMARKS  <br/> |
|Cache Deferred Columns  <br/> |DBPROP_CACHEDEFERRED  <br/> |
|Change Inserted Rows  <br/> |DBPROP_CHANGEINSERTEDROWS  <br/> |
|Column Privileges  <br/> |DBPROP_COLUMNRESTRICT  <br/> |
|Column Set Notification  <br/> |DBPROP_NOTIFYCOLUMNSET  <br/> |
|Column Writable  <br/> |DBPROP_MAYWRITECOLUMN  <br/> |
|Defer Column  <br/> |DBPROP_DEFERRED  <br/> |
|Delay Storage Object Updates  <br/> |DBPROP_DELAYSTORAGEOBJECTS  <br/> |
|Fetch Backwards  <br/> |DBPROP_CANFETCHBACKWARDS  <br/> |
|Hold Rows  <br/> |DBPROP_CANHOLDROWS  <br/> |
|IAccessor  <br/> |DBPROP_IAccessor  <br/> |
|IColumnsInfo  <br/> |DBPROP_IColumnsInfo  <br/> |
|IColumnsRowset  <br/> |DBPROP_IColumnsRowset  <br/> |
|IConnectionPointContainer  <br/> |DBPROP_IConnectionPointContainer  <br/> |
|IConvertType  <br/> |DBPROP_IConvertType  <br/> |
|ILockBytes  <br/> |DBPROP_ILockBytes  <br/> |
|Immobile Rows  <br/> |DBPROP_IMMOBILEROWS  <br/> |
|IRowset  <br/> |DBPROP_IRowset  <br/> |
|IRowsetChange  <br/> |DBPROP_IRowsetChange  <br/> |
|IRowsetIdentity  <br/> |DBPROP_IRowsetIdentity  <br/> |
|IRowsetIndex  <br/> |DBPROP_IRowsetIndex  <br/> |
|IRowsetInfo  <br/> |DBPROP_IRowsetInfo  <br/> |
|IRowsetLocate  <br/> |DBPROP_IRowsestLocate  <br/> |
|IRowsetResynch  <br/> ||
|IRowsetScroll  <br/> |DBPROP_IRowsetScroll  <br/> |
|IRowsetUpdate  <br/> |DBPROP_IRowsetUpdate  <br/> |
|ISequentialStream  <br/> |DBPROP_ISequentialStream  <br/> |
|IStorage  <br/> |DBPROP_IStorage  <br/> |
|IStream  <br/> |DBPROP_IStream  <br/> |
|ISupportErrorInfo  <br/> |DBPROP_ISupportErrorInfo  <br/> |
|Literal Bookmarks  <br/> |DBPROP_LITERALBOOKMARKS  <br/> |
|Literal Row Identity  <br/> |DBPROP_LITERALIDENTITY  <br/> |
|Maximum Open Rows  <br/> |DBPROP_MAXOPENROWS  <br/> |
|Maximum Pending Rows  <br/> |DBPROP_MAXPENDINGROWS  <br/> |
|Maximum Rows  <br/> |DBPROP_MAXROWS  <br/> |
|Memory Usage  <br/> |DBPROP_MEMORYUSAGE  <br/> |
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
|Skip Deleted Bookmarks  <br/> |DBPROP_BOOKMARKSKIPPED  <br/> |
|Strong Row Identity  <br/> |DBPROP_STRONGITDENTITY  <br/> |
|Updatability  <br/> |DBPROP_UPDATABILITY  <br/> |
|Use Bookmarks  <br/> |DBPROP_BOOKMARKS  <br/> |
   
## Command Dynamic Properties

The following properties are added to the **Command** object's **Properties** collection. 
  
|**ADO Property Name**|**OLE DB Property Name**|
|:-----|:-----|
|Access Order  <br/> |DBPROP_ACCESSORDER  <br/> |
|Append-Only Rowset  <br/> |DBPROP_APPENDONLY  <br/> |
|Blocking Storage Objects  <br/> |DBPROP_BLOCKINGSTORAGEOBJECTS  <br/> |
|Bookmark Type  <br/> |DBPROP_BOOKMARKTYPE  <br/> |
|Bookmarkable  <br/> |DBPROP_IROWSETLOCATE  <br/> |
|Change Inserted Rows  <br/> |DBPROP_CHANGEINSERTEDROWS  <br/> |
|Column Privileges  <br/> |DBPROP_COLUMNRESTRICT  <br/> |
|Column Set Notification  <br/> |DBPROP_NOTIFYCOLUMNSET  <br/> |
|Defer Column  <br/> |DBPROP_DEFERRED  <br/> |
|Delay Storage Object Updates  <br/> |DBPROP_DELAYSTORAGEOBJECTS  <br/> |
|Fetch Backwards  <br/> |DBPROP_CANFETCHBACKWARDS  <br/> |
|Hold Rows  <br/> |DBPROP_CANHOLDROWS  <br/> |
|IAccessor  <br/> |DBPROP_IAccessor  <br/> |
|IColumnsInfo  <br/> |DBPROP_IColumnsInfo  <br/> |
|IColumnsRowset  <br/> |DBPROP_IColumnsRowset  <br/> |
|IConnectionPointContainer  <br/> |DBPROP_IConnectionPointContainer  <br/> |
|IConvertType  <br/> |DBPROP_IConvertType  <br/> |
|ILockBytes  <br/> |DBPROP_ILockBytes  <br/> |
|Immobile Rows  <br/> |DBPROP_IMMOBILEROWS  <br/> |
|IRowset  <br/> |DBPROP_IRowset  <br/> |
|IRowsetChange  <br/> |DBPROP_IRowsetChange  <br/> |
|IRowsetIdentity  <br/> |DBPROP_IRowsetIdentity  <br/> |
|IRowsetIndex  <br/> |DBPROP_IRowsetIndex  <br/> |
|IRowsetInfo  <br/> |DBPROP_IRowsetInfo  <br/> |
|IRowsetLocate  <br/> |DBPROP_IRowsetLocate  <br/> |
|IRowsetResynch  <br/> ||
|IRowsetScroll  <br/> |DBPROP_IRowsetScroll  <br/> |
|IRowsetUpdate  <br/> |DBPROP_IRowsetUpdate  <br/> |
|ISequentialStream  <br/> |DBPROP_ISequentialStream  <br/> |
|IStorage  <br/> |DBPROP_IStorage  <br/> |
|IStream  <br/> |DBPROP_IStream  <br/> |
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
|Server Data on Insert  <br/> |DBPROP_SERVERDATAONINSERT  <br/> |
|Skip Deleted Bookmarks  <br/> |DBPROP_BOOKMARKSKIP  <br/> |
|Strong Row Identity  <br/> |DBPROP_STRONGIDENTITY  <br/> |
|Updatability  <br/> |DBPROP_UPDATABILITY  <br/> |
|Use Bookmarks  <br/> |DBPROP_BOOKMARKS  <br/> |
   
 **See Also** For specific implementation details and functional information about the OLE DB Provider for Microsoft Jet, consult the OLE DB Provider for Microsoft Jet documentation in the MDAC SDK. 
  

