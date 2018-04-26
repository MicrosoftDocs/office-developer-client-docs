---
title: "Microsoft OLE DB Provider for ODBC"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: c507567e-5ad1-b32a-f6ad-5ba2c39aa4c2

description: "To an ADO or RDS programmer, an ideal world would be one in which every data source exposes an OLE DB interface, so that ADO could call directly into the data source. Although increasingly more database vendors are implementing OLE DB interfaces, some data sources are not yet exposed this way. However, virtually all DBMS systems in use today can be accessed through ODBC."
---

# Microsoft OLE DB Provider for ODBC

To an ADO or RDS programmer, an ideal world would be one in which every data source exposes an OLE DB interface, so that ADO could call directly into the data source. Although increasingly more database vendors are implementing OLE DB interfaces, some data sources are not yet exposed this way. However, virtually all DBMS systems in use today can be accessed through ODBC.
  
ODBC drivers are available for every major DBMS in use today, including Microsoft SQL Server, Microsoft Access (Microsoft Jet database engine), and Microsoft FoxPro, in addition to non-Microsoft database products such as Oracle.
  
The Microsoft ODBC Provider, however, allows ADO to connect to any ODBC data source. The provider is free-threaded and Unicode enabled.
  
The provider supports transactions, although different DBMS engines offer different types of transaction support. For example, Microsoft Access supports nested transactions up to five levels deep.
  
This is the default provider for ADO, and all provider-dependent ADO properties and methods are supported.
  
## Connection String Parameters

To connect to this provider, set the **Provider=** argument of the [ConnectionString](connectionstring-property-ado.md) property to: 
  
```
 
MSDASQL 

```

Reading the [Provider](provider-property-ado.md) property will return this string as well. 
  
## Typical Connection String

A typical connection string for this provider is:
  
```
 
"Provider=MSDASQL;DSN=dsnName ;UID=userName ;PWD=userPassword ;" 

```

The string consists of these keywords:
  
|**Keyword**|**Description**|
|:-----|:-----|
|**Provider** <br/> |Specifies the OLE DB Provider for ODBC.  <br/> |
|**DSN** <br/> |Specifies the data source name.  <br/> |
|**UID** <br/> |Specifies the user name.  <br/> |
|**PWD** <br/> |Specifies the user password.  <br/> |
|**URL** <br/> |Specifies the URL of a file or directory published in a Web folder.  <br/> |
   
Because this is the default provider for ADO, if you omit the **Provider=** parameter from the connection string, ADO will attempt to establish a connection to this provider. 
  
The provider does not support any specific connection parameters in addition to those defined by ADO. However, the provider will pass any non-ADO connection parameters to the ODBC driver manager.
  
Because you can omit the **Provider** parameter, you can therefore compose an ADO connection string that is identical to an ODBC connection string for the same data source. Use the same parameter names ( **DRIVER=**, **DATABASE=**, **DSN=**, and so on), values, and syntax as you would when composing an ODBC connection string. You can connect with or without a predefined data source name (DSN) or FileDSN. 
  
 **Syntax with a DSN or FileDSN:**
  
```
"[Provider=MSDASQL;] { DSN=name  | FileDSN=filename  } ;  
[DATABASE=database;] UID=user;PWD=password"
```

 **Syntax without a DSN (DSN-less connection):**
  
```
"[Provider=MSDASQL;] DRIVER=driver;SERVER=server;DATABASE=database;UID=user;PWD=password"
```

If you use a **DSN** or **FileDSN**, it must be defined through the ODBC Data Source Administrator in the Windows Control Panel. In Microsoft Windows 2000, the ODBC Administrator is located under Administrative Tools. In previous versions of Windows, the ODBC Administrator icon is named **32-bit ODBC** or simply **ODBC**. 
  
As an alternative to setting a **DSN**, you can specify the ODBC driver ( **DRIVER=** ), such as "SQL Server;" the server name ( **SERVER=** ); and the database name ( **DATABASE=** ). 
  
You can also specify a user account name ( **UID=** ), and the password for the user account ( **PWD=** ) in the ODBC-specific parameters or in the standard ADO-defined  *user*  and  *password*  parameters. 
  
Although a **DSN** definition already specifies a database, you can specify  *a*  *database*  parameter in addition to a **DSN** to connect to a different database. It is a good idea to always include  *the*  *database*  parameter when you use a **DSN**. This will ensure that you connect to the proper database in the event that another user changed the default database parameter since you last checked the **DSN** definition. 
  
## Provider-Specific Connection Properties

The OLE DB provider for ODBC adds several properties to the [Properties](properties-collection-ado.md) collection of the **Connection** object. The following table lists these properties with the corresponding OLE DB property name in parentheses. 
  
|**Property Name**|**Description**|
|:-----|:-----|
|Accessible Procedures           (KAGPROP_ACCESSIBLEPROCEDURES)  <br/> |Indicates whether the user has access to stored procedures.  <br/> |
|Accessible Tables           (KAGPROP_ACCESSIBLETABLES)  <br/> |Indicates whether the user has permission to execute SELECT statements against the database tables.  <br/> |
|Active Statements           (KAGPROP_ACTIVESTATEMENTS)  <br/> |Indicates the number of handles an ODBC driver can support on a connection.  <br/> |
|Driver Name           (KAGPROP_DRIVERNAME)  <br/> |Indicates the file name of the ODBC driver.  <br/> |
|Driver ODBC Version           (KAGPROP_DRIVERODBCVER)  <br/> |Indicates the version of ODBC that this driver supports.  <br/> |
|File Usage           (KAGPROP_FILEUSAGE)  <br/> |Indicates how the driver treats a file in a data source; as a table or as a catalog.  <br/> |
|Like Escape Clause           (KAGPROP_LIKEESCAPECLAUSE)  <br/> |Indicates whether the driver supports the definition and use of an escape character for the percent character (%) and underline character (_) in the LIKE predicate of a WHERE clause.  <br/> |
|Max Columns in Group By           (KAGPROP_MAXCOLUMNSINGROUPBY)  <br/> |Indicates the maximum number of columns that can be listed in the GROUP BY clause of a SELECT statement.  <br/> |
|Max Columns in Index           (KAGPROP_MAXCOLUMNSININDEX)  <br/> |Indicates the maximum number of columns that can be included in an index.  <br/> |
|Max Columns in Order By           (KAGPROP_MAXCOLUMNSINORDERBY)  <br/> |Indicates the maximum number of columns that can be listed in the ORDER BY clause of a SELECT statement.  <br/> |
|Max Columns in Select           (KAGPROP_MAXCOLUMNSINSELECT)  <br/> |Indicates the maximum number of columns that can be listed in the SELECT portion of a SELECT statement.  <br/> |
|Max Columns in Table           (KAGPROP_MAXCOLUMNSINTABLE)  <br/> |Indicates the maximum number of columns allowed in a table.  <br/> |
|Numeric Functions           (KAGPROP_NUMERICFUNCTIONS)  <br/> |Indicates which numeric functions are supported by the ODBC driver. For a listing of function names and the associated values used in this bitmask, see Appendix E: Scalar Functions in the ODBC documentation.  <br/> |
|Outer Join Capabilities           (KAGPROP_OJCAPABILITY)  <br/> |Indicates the types of OUTER JOINs supported by the provider.  <br/> |
|Outer Joins           (KAGPROP_OUTERJOINS)  <br/> |Indicates whether the provider supports OUTER JOINs.  <br/> |
|Special Characters           (KAGPROP_SPECIALCHARACTERS)  <br/> |Indicates which characters have special meaning for the ODBC driver.  <br/> |
|Stored Procedures           (KAGPROP_PROCEDURES)  <br/> |Indicates whether stored procedures are available for use with this ODBC driver.  <br/> |
|String Functions           (KAGPROP_STRINGFUNCTIONS)  <br/> |Indicates which string functions are supported by the ODBC driver. For a listing of function names and the associated values used in this bitmask, see Appendix E: Scalar Functions in the ODBC documentation.  <br/> |
|System Functions           (KAGPROP_SYSTEMFUNCTIONS)  <br/> |Indicates which system functions are supported by the ODBC driver. For a listing of function names and the associated values used in this bitmask, see Appendix E: Scalar Functions in the ODBC documentation.  <br/> |
|Time/Date Functions           (KAGPROP_TIMEDATEFUNCTIONS)  <br/> |Indicates which time and date functions are supported by the ODBC driver. For a listing of function names and the associated values used in this bitmask, see Appendix E: Scalar Functions in the ODBC documentation.  <br/> |
|SQL Grammar Support           (KAGPROP_ODBCSQLCONFORMANCE)  <br/> |Indicates the SQL grammar that the ODBC driver supports.  <br/> |
   
## Provider-Specific Recordset and Command Properties

The OLE DB provider for ODBC adds several properties to the **Properties** collection of the **Recordset** and **Command** objects. The following table lists these properties with the corresponding OLE DB property name in parentheses. 
  
|**Property Name**|**Description**|
|:-----|:-----|
|Query Based Updates/Deletes/Inserts           (KAGPROP_QUERYBASEDUPDATES)  <br/> |Indicates whether updates, deletions, and insertions can be performed using SQL queries.  <br/> |
|ODBC Concurrency Type           (KAGPROP_CONCURRENCY)  <br/> |Indicates the method used to reduce potential problems caused by two users attempting to access the same data from the data source simultaneously.  <br/> |
|BLOB accessibility on Forward-Only cursor           (KAGPROP_BLOBSONFOCURSOR)  <br/> |Indicates whether BLOB **Fields** can be accessed when using a forward-only cursor.  <br/> |
|Include SQL_FLOAT, SQL_DOUBLE, and SQL_REAL in QBU WHERE clauses           (KAGPROP_INCLUDENONEXACT)  <br/> |Indicates whether SQL_FLOAT, SQL_DOUBLE, and SQL_REAL values can be included in a QBU WHERE clause.  <br/> |
|Position on the last row after insert           (KAGPROP_POSITIONONNEWROW)  <br/> |Indicates that after a new record has been inserted in a table, the last row in the table will be come the current row.  <br/> |
|IRowsetChangeExtInfo           (KAGPROP_IROWSETCHANGEEXTINFO)  <br/> |Indicates whether the **IRowsetChange** interface provides extended information support.  <br/> |
|ODBC Cursor Type           (KAGPROP_CURSOR)  <br/> |Indicates the type of cursor used by the **Recordset**.  <br/> |
|Generate a Rowset that can be marshaled           (KAGPROP_MARSHALLABLE)  <br/> |Indicates that the ODBC driver generates a recordset that can be marshaled  <br/> |
   
## Command Text

How you use the [Command](command-object-ado.md) object largely depends on the data source, and what type of query or command statement it will accept. 
  
ODBC provides a specific syntax for calling stored procedures. For the [CommandText](commandtext-property-ado.md) property of a **Command** object, the  *CommandText*  argument to the **Execute** method on a [Connection](connection-object-ado.md) object, or the  *Source*  argument to the **Open** method on a [Recordset](recordset-object-ado.md) object, passes in a string with this syntax: 
  
```
"{ [ ? = ] callprocedure  [ (? [, ? [ ,  ]] ) ] }"
```

Each **?** references an object in the [Parameters](parameters-collection-ado.md) collection. The first **?** references **Parameters** (0), the next **?** references **Parameters** (1), and so on. 
  
The parameter references are optional and depend on the structure of the stored procedure. If you want to call a stored procedure that defines no parameters, your string would look like this:
  
```
"{callprocedure }"
```

If you have two query parameters, your string would look like this:
  
```
"{ callprocedure ( ?, ? ) }"
```

If the stored procedure will return a value, the return value is treated as another parameter. If you have no query parameters but you do have a return value, your string would look like this:
  
```
"{ ? = callprocedure }"
```

Finally, if you have a return value and two query parameters, your string would look like this:
  
```
"{ ? = callprocedure( ?, ? ) }"
```

## Recordset Behavior

The following tables list the standard ADO methods and properties available on a **Recordset** object opened with this provider. 
  
For more detailed information about **Recordset** behavior for your provider configuration, run the [Supports](supports-method-ado.md) method and enumerate the **Properties** collection of the **Recordset** to determine whether provider-specific dynamic properties are present. 
  
Availability of standard ADO **Recordset** properties: 
  
|**Property**|**ForwardOnly**|**Dynamic**|**Keyset**|**Static**|
|:-----|:-----|:-----|:-----|:-----|
|[AbsolutePage](absolutepage-property-ado.md) <br/> |not available  <br/> |not available  <br/> |read/write  <br/> |read/write  <br/> |
|[AbsolutePosition](absoluteposition-property-ado.md) <br/> |not available  <br/> |not available  <br/> |read/write  <br/> |read/write  <br/> |
|[ActiveConnection](activeconnection-property-ado.md) <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |
|[BOF](bof-eof-properties-ado.md) <br/> |read-only  <br/> |read-only  <br/> |read-only  <br/> |read-only  <br/> |
|[Bookmark](bookmark-property-ado.md) <br/> |not available  <br/> |not available  <br/> |read/write  <br/> |read/write  <br/> |
|[CacheSize](cachesize-property-ado.md) <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |
|[CursorLocation](cursorlocation-property-ado.md) <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |
|[CursorType](cursortype-property-ado.md) <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |
|[EditMode](editmode-property-ado.md) <br/> |read-only  <br/> |read-only  <br/> |read-only  <br/> |read-only  <br/> |
|[Filter](filter-property-ado.md) <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |
|[LockType](locktype-property-ado.md) <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |
|[MarshalOptions](marshaloptions-property-ado.md) <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |
|[MaxRecords](maxrecords-property-ado.md) <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |
|[PageCount](pagecount-property-ado.md) <br/> |read/write  <br/> |not available  <br/> |read-only  <br/> |read-only  <br/> |
|[PageSize](pagesize-property-ado.md) <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |
|[RecordCount](recordcount-property-ado.md) <br/> |read/write  <br/> |not available  <br/> |read-only  <br/> |read-only  <br/> |
|[Source](source-property-ado-recordset.md) <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |read/write  <br/> |
|[State](state-property-ado.md) <br/> |read-only  <br/> |read-only  <br/> |read-only  <br/> |read-only  <br/> |
|[Status](status-property-ado-recordset.md) <br/> |read-only  <br/> |read-only  <br/> |read-only  <br/> |read-only  <br/> |
   
The [AbsolutePosition](absoluteposition-property-ado.md) and [AbsolutePage](absolutepage-property-ado.md) properties are write-only when ADO is used with version 1.0 of the Microsoft OLE DB Provider for ODBC. 
  
Availability of standard ADO **Recordset** methods: 
  
|**Method**|**ForwardOnly**|**Dynamic**|**Keyset**|**Static**|
|:-----|:-----|:-----|:-----|:-----|
|[AddNew](addnew-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[Cancel](cancel-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[CancelBatch](cancelbatch-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[CancelUpdate](cancelupdate-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[Clone](clone-method-ado.md) <br/> |No  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|[Close](close-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[Delete](delete-method-ado-recordset.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[GetRows](getrows-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[Move](move-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[MoveLast](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[MoveNext](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[MovePrevious](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[NextRecordset](nextrecordset-method-ado.md)\*  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[Open](open-method-ado-recordset.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[Requery](requery-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[Resync](resync-method-ado.md) <br/> |No  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|[Supports](supports-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[Update](update-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|[UpdateBatch](updatebatch-method-ado.md) <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
   
\*Not supported for Microsoft Access databases.
  
## Dynamic Properties

The Microsoft OLE DB Provider for ODBC inserts several dynamic properties into the **Properties** collection of the unopened [Connection](connection-object-ado.md), [Recordset](recordset-object-ado.md), and [Command](command-object-ado.md) objects. 
  
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
|Location  <br/> |DBPROP_INIT_LOCATION  <br/> |
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
|OLE DB Services  <br/> |DBPROP_INIT_OLEDBSERVICES  <br/> |
|OLE DB Version  <br/> |DBPROP_PROVIDEROLEDBVER  <br/> |
|OLE Object Support  <br/> |DBPROP_OLEOBJECTS  <br/> |
|Open Rowset Support  <br/> |DBPROP_OPENROWSETSUPPORT  <br/> |
|ORDER BY Columns in Select List  <br/> |DBPROP_ORDERBYCOLUMNSINSELECT  <br/> |
|Output Parameter Availability  <br/> |DBPROP_OUTPUTPARAMETERAVAILABILITY  <br/> |
|Password  <br/> |DBPROP_AUTH_PASSWORD  <br/> |
|Pass By Ref Accessors  <br/> |DBPROP_BYREFACCESSORS  <br/> |
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
|IRowsetResynch  <br/> ||
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
|Unique Rows  <br/> |DBPROP_UNIQUEROWS  <br/> |
|Updatability  <br/> |DBPROP_UPDATABILITY  <br/> |
|Use Bookmarks  <br/> |DBPROP_BOOKMARKS  <br/> |
   
## Command Dynamic Properties

The following properties are added to the **Command** object's **Properties** collection. 
  
|**ADO Property Name**|**OLE DB Property Name**|
|:-----|:-----|
|Access Order  <br/> |DBPROP_ACCESSORDER  <br/> |
|Blocking Storage Objects  <br/> |DBPROP_BLOCKINGSTORAGEOBJECTS  <br/> |
|Bookmark Type  <br/> |DBPROP_BOOKMARKTYPE  <br/> |
|Bookmarkable  <br/> |DBPROP_IROWSETLOCATE  <br/> |
|Change Inserted Rows  <br/> |DBPROP_CHANGEINSERTEDROWS  <br/> |
|Column Privileges  <br/> |DBPROP_COLUMNRESTRICT  <br/> |
|Column Set Notification  <br/> |DBPROP_NOTIFYCOLUMNSET  <br/> |
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
|IRowsetResynch  <br/> ||
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
|Skip Deleted Bookmarks  <br/> |DBPROP_BOOKMARKSKIP  <br/> |
|Strong Row Identity  <br/> |DBPROP_STRONGIDENTITY  <br/> |
|Updatability  <br/> |DBPROP_UPDATABILITY  <br/> |
|Use Bookmarks  <br/> |DBPROP_BOOKMARKS  <br/> |
   
 **See Also** For details regarding specific implementation and functional information about the Microsoft OLE DB Provider for ODBC, consult the [OLE DB Programmer's Guide](http://msdn.microsoft.com/en-us/library/ms713643%28VS.85%29.aspx) or visit the [Data Platform Developer Center](http://msdn.microsoft.com/en-us/data/default.aspx).
  

