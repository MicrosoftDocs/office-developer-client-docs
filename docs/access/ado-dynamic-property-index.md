---
title: "ADO Dynamic Property Index"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 437beced-b97a-894d-b08f-4a322629a5a6
description: "Data providers, service providers, and service components can add dynamic properties to the Properties collections of the unopened Connection and Recordset objects. A given provider may also insert additional properties when these objects are opened. Some of these properties are listed in the ADO Dynamic Properties section. More are listed under the specific providers in the Appendix A: Providers section."
---

# ADO Dynamic Property Index

Data providers, service providers, and service components can add dynamic properties to the **Properties** collections of the unopened [Connection](connection-object-ado.md) and [Recordset](recordset-object-ado.md) objects. A given provider may also insert additional properties when these objects are opened. Some of these properties are listed in the [ADO Dynamic Properties](ado-dynamic-properties.md) section. More are listed under the specific providers in the [Appendix A: Providers](appendix-a-providers.md) section. 
  
The table below is a cross-index of the ADO and OLE DB names for each standard OLE DB provider dynamic property. Your providers may add more properties than listed here. For the specific information about provider-specific dynamic properties, see your provider documentation.
  
The OLE DB Programmer's Reference refers to an ADO property name by the term, "Description." You can find more information about these standard properties in the OLE DB Programmer's Reference. Search for the OLE DB property name in the Index or see the following topics:
  
- Appendix C: OLE DB Properties
    
- Supported Properties of the Cursor Service
    
- Supported Properties of the Persistence Provider
    
- Supported OLE DB Properties of the Remoting Provider
    
## Remarks

Note numbers used in the cross-index:
  
(1) This property is a Boolean flag indicating whether the named interface should be used. The equivalent OLE DB property name is listed if it exists.
  
(2) The "Bookmarkable" ADO property is generated internally for backwards compatibility, and is mapped to the OLE DB property, DBPROP_IROWSETLOCATE. This is the same property that corresponds to the ADO property, IRowsetLocate.
  
(3) The ADO property name, "Hidden Columns", is named differently than the OLE DB property name Description, "Hidden Columns Count."
  
(4) For hierarchical recordsets, the "Maximum Rows" ADO property gets applied across all children. Depending on the order in which the rows are returned, you might have all, some or no children for each parent or orphaned children in the result set. Therefore, when reshaping hierarchical recordsets, the identifier for every child should be unique. In general, the [Microsoft Data Shaping Service for OLE DB (MSDATASHAPE)](microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) provider does not allow for distinction between properties that can be inherited from the parent and those that cannot be inherited. 
  
(5) Does not apply.
  
 **Connection Dynamic Properties**
  
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
   
 **Recordset Dynamic Properties**
  
Note that the **Dynamic Properties** of the **Recordset** object go out of scope (become unavailable) when the **Recordset** is closed. 
  
|**ADO Property Name**|**OLE DB Property Name**|
|:-----|:-----|
|IAccessor  <br/> |DBPROP_IACCESSOR [(1)](#mdadyn_remarks) <br/> |
|IChapteredRowset  <br/> |[(1)](#mdadyn_remarks) <br/> |
|IColumnsInfo  <br/> |DBPROP_ICOLUMNSINFO [(1)](#mdadyn_remarks) <br/> |
|IColumnsRowset  <br/> |DBPROP_ICOLUMNSROWSET [(1)](#mdadyn_remarks) <br/> |
|IConnectionPointContainer  <br/> |DBPROP_ICONNECTIONPOINTCONTAINER [(1)](#mdadyn_remarks) <br/> |
|IConvertType  <br/> |[(1)](#mdadyn_remarks) <br/> |
|ILockBytes  <br/> |DBPROP_ILOCKBYTES [(1)](#mdadyn_remarks) <br/> |
|IRowset  <br/> |DBPROP_IROWSET [(1)](#mdadyn_remarks) <br/> |
|IDBAsynchStatus  <br/> |DBPROP_IDBASYNCHSTATUS [(1)](#mdadyn_remarks) <br/> |
|IParentRowset  <br/> |[(1)](#mdadyn_remarks) <br/> |
|IRowsetChange  <br/> |DBPROP_IROWSETCHANGE [(1)](#mdadyn_remarks) <br/> |
|IRowsetExactScroll  <br/> |[(1)](#mdadyn_remarks) <br/> |
|IRowsetFind  <br/> |DBPROP_IROWSETFIND [(1)](#mdadyn_remarks) <br/> |
|IRowsetIdentity  <br/> |DBPROP_IROWSETIDENTITY [(1)](#mdadyn_remarks) <br/> |
|IRowsetInfo  <br/> |DBPROP_IROWSETINFO [(1)](#mdadyn_remarks) <br/> |
|IRowsetLocate  <br/> |DBPROP_IROWSETLOCATE [(1)](#mdadyn_remarks) <br/> |
|IRowsetRefresh  <br/> |DBPROP_IROWSETREFRESH [(1)](#mdadyn_remarks) <br/> |
|IRowsetResynch  <br/> |[(1)](#mdadyn_remarks) <br/> |
|IRowsetScroll  <br/> |DBPROP_IROWSETSCROLL [(1)](#mdadyn_remarks) <br/> |
|IRowsetUpdate  <br/> |DBPROP_IROWSETUPDATE [(1)](#mdadyn_remarks) <br/> |
|IRowsetView  <br/> |DBPROP_IROWSETVIEW [(1)](#mdadyn_remarks) <br/> |
|IRowsetIndex  <br/> |DBPROP_IROWSETINDEX [(1)](#mdadyn_remarks) <br/> |
|ISequentialStream  <br/> |DBPROP_ISEQUENTIALSTREAM [(1)](#mdadyn_remarks) <br/> |
|IStorage  <br/> |DBPROP_ISTORAGE [(1)](#mdadyn_remarks) <br/> |
|IStream  <br/> |DBPROP_ISTREAM [(1)](#mdadyn_remarks) <br/> |
|ISupportErrorInfo  <br/> |DBPROP_ISUPPORTERRORINFO [(1)](#mdadyn_remarks) <br/> |
|Access Order  <br/> |DBPROP_ACCESSORDER  <br/> |
|Append-Only Rowset  <br/> |DBPROP_APPENDONLY  <br/> |
|Asynchronous Rowset Processing  <br/> |DBPROP_ROWSET_ASYNCH  <br/> |
|Auto Recalc  <br/> |DBPROP_ADC_AUTORECALC  <br/> |
|Background Fetch Size  <br/> |DBPROP_ASYNCHFETCHSIZE  <br/> |
|Background Thread Priority  <br/> |DBPROP_ASYNCHTHREADPRIORITY  <br/> |
|Batch Size  <br/> |DBPROP_ADC_BATCHSIZE  <br/> |
|Blocking Storage Objects  <br/> |DBPROP_BLOCKINGSTORAGEOBJECTS  <br/> |
|Bookmark Type  <br/> |DBPROP_BOOKMARKTYPE  <br/> |
|Bookmarkable  <br/> |DBPROP_IROWSETLOCATE [(2)](#mdadyn_remarks) <br/> |
|Bookmarks Ordered  <br/> |DBPROP_ORDEREDBOOKMARKS  <br/> |
|Cache Child Rows  <br/> |DBPROP_ADC_CACHECHILDROWS  <br/> |
|Cache Deferred Columns  <br/> |DBPROP_CACHEDEFERRED  <br/> |
|Change Inserted Rows  <br/> |DBPROP_CHANGEINSERTEDROWS  <br/> |
|Column Privileges  <br/> |DBPROP_COLUMNRESTRICT  <br/> |
|Column Set Notification  <br/> |DBPROP_NOTIFYCOLUMNSET  <br/> |
|Column Writable  <br/> |DBPROP_MAYWRITECOLUMN  <br/> |
|Command Time Out  <br/> |DBPROP_COMMANDTIMEOUT  <br/> |
|Cursor Engine Version  <br/> |DBPROP_ADC_CEVER  <br/> |
|Defer Column  <br/> |DBPROP_DEFERRED  <br/> |
|Delay Storage Object Updates  <br/> |DBPROP_DELAYSTORAGEOBJECTS  <br/> |
|Fetch Backwards  <br/> |DBPROP_CANFETCHBACKWARDS  <br/> |
|Filter Operations  <br/> |DBPROP_FILTERCOMPAREOPS  <br/> |
|Find Operations  <br/> |DBPROP_FINDCOMPAREOPS  <br/> |
|Hidden Columns (Count)  <br/> |DBPROP_HIDDENCOLUMNS [(3)](#mdadyn_remarks) <br/> |
|Hold Rows  <br/> |DBPROP_CANHOLDROWS  <br/> |
|Immobile Rows  <br/> |DBPROP_IMMOBILEROWS  <br/> |
|Initial Fetch Size  <br/> |DBPROP_ASYNCHPREFETCHSIZE  <br/> |
|Literal Bookmarks  <br/> |DBPROP_LITERALBOOKMARKS  <br/> |
|Literal Row Identity  <br/> |DBPROP_LITERALIDENTITY  <br/> |
|Maintain Change Status  <br/> |DBPROP_ADC_MAINTAINCHANGESTATUS  <br/> |
|Maximum Open Rows  <br/> |DBPROP_MAXOPENROWS  <br/> |
|Maximum Pending Rows  <br/> |DBPROP_MAXPENDINGROWS  <br/> |
|Maximum Rows  <br/> |DBPROP_MAXROWS [(4)](#mdadyn_remarks) <br/> |
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
|Private1  <br/> |[(5)](#mdadyn_remarks) <br/> |
|Quick Restart  <br/> |DBPROP_QUICKRESTART  <br/> |
|Reentrant Events  <br/> |DBPROP_REENTRANTEVENTS  <br/> |
|Remove Deleted Rows  <br/> |DBPROP_REMOVEDELETED  <br/> |
|Report Multiple Changes  <br/> |DBPROP_REPORTMULTIPLECHANGES  <br/> |
|Reshape Name  <br/> |DBPROP_ADC_RESHAPENAME  <br/> |
|Resync Command  <br/> |DBPROP_ADC_CUSTOMRESYNCH  <br/> |
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
|Skip Deleted Bookmarks  <br/> |DBPROP_BOOKMARKSKIPPED  <br/> |
|Strong Row Identity  <br/> |DBPROP_STRONGIDENTITY  <br/> |
|Unique Catalog  <br/> |DBPROP_ADC_UNIQUECATALOG  <br/> |
|Unique Rows  <br/> |DBPROP_UNIQUEROWS  <br/> |
|Unique Schema  <br/> |DBPROP_ADC_UNIQUESCHEMA  <br/> |
|Unique Table  <br/> |DBPROP_ADC_UNIQUETABLE  <br/> |
|Updatability  <br/> |DBPROP_UPDATABILITY  <br/> |
|Update Criteria  <br/> |DBPROP_ADC_UPDATECRITERIA  <br/> |
|Update Resync  <br/> |DBPROP_ADC_UPDATERESYNC  <br/> |
|Use Bookmarks  <br/> |DBPROP_BOOKMARKS  <br/> |
   

