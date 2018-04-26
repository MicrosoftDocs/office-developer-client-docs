---
title: "Microsoft OLE DB Provider for Microsoft Indexing Service"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 01c2e75c-950a-dd8a-2b20-bbd916315ec5
description: "The Microsoft OLE DB Provider for Microsoft Indexing Service provides programmatic read-only access to file system and Web data indexed by Microsoft Indexing Service. ADO applications can issue SQL queries to retrieve content and file property information."
---

# Microsoft OLE DB Provider for Microsoft Indexing Service

The Microsoft OLE DB Provider for Microsoft Indexing Service provides programmatic read-only access to file system and Web data indexed by Microsoft Indexing Service. ADO applications can issue SQL queries to retrieve content and file property information.
  
The provider is free-threaded and unicode enabled.
  
## Connection String Parameters

To connect to this provider, set the **Provider=** argument to the [ConnectionString](connectionstring-property-ado.md) property to: 
  
```
 
MSIDXS 

```

Reading the [Provider](provider-property-ado.md) property will return this string as well. 
  
## Typical Connection String

A typical connection string for this provider is:
  
```
 
"Provider=MSIDXS;Data Source=myCatalog ;Locale Identifier=nnnn ;" 

```

The string consists of these keywords:
  
|**Keyword**|**Description**|
|:-----|:-----|
|**Provider** <br/> |Specifies the OLE DB Provider for Microsoft Indexing Service. Typically this is the only keyword specified in the connection string.  <br/> |
|**Data Source** <br/> |Specifies the Indexing Service catalog name. If this keyword is not specified, the default system catalog is used.  <br/> |
|**Locale Identifier** <br/> |Specifies a unique 32-bit number (for example, 1033) that specifies preferences related to the user's language. These preferences indicate how dates and times are formatted, items are sorted alphabetically, strings are compared, and so on. If this keyword is not specified, the default system locale identifier is used.  <br/> |
   
## Command Text

The Indexing Service SQL query syntax consists of extensions to the SQL-92 **SELECT** statement and its **FROM** and **WHERE** clauses. The results of the query are returned via OLE DB rowsets, which can be consumed by ADO and manipulated as [Recordset](recordset-object-ado.md) objects. 
  
You can search for exact words or phrases, or use wildcards to search for patterns or stems of words. The search logic can be based on Boolean decisions, weighted terms, or proximity to other words. You can also search by "free text," which finds matches based on meaning, rather than exact words.
  
The provider does not accept stored procedure calls or simple table names (for example, the [CommandType](commandtype-property-ado.md) property will always be **adCmdText** ). 
  
## Recordset Behavior

The following tables list the features available with a **Recordset** object opened with this provider. Only the Static cursor type ( **adOpenStatic** ) is available. 
  
For more detailed information about **Recordset** behavior for your provider configuration, run the [Supports](supports-method-ado.md) method and enumerate the [Properties](properties-collection-ado.md) collection of the **Recordset** to determine whether provider-specific dynamic properties are present. 
  
Availability of standard ADO **Recordset** properties: 
  
|**Property**|**Availability**|
|:-----|:-----|
|[AbsolutePage](absolutepage-property-ado.md) <br/> |read/write  <br/> |
|[AbsolutePosition](absoluteposition-property-ado.md) <br/> |read/write  <br/> |
|[ActiveConnection](activeconnection-property-ado.md) <br/> |read-only  <br/> |
|[BOF](bof-eof-properties-ado.md) <br/> |read-only  <br/> |
|[Bookmark](bookmark-property-ado.md)\*  <br/> |read/write  <br/> |
|[CacheSize](cachesize-property-ado.md) <br/> |read/write  <br/> |
|[CursorLocation](cursorlocation-property-ado.md) <br/> |always **adUseServer** <br/> |
|[CursorType](cursortype-property-ado.md) <br/> |always **adOpenStatic** <br/> |
|[EditMode](editmode-property-ado.md) <br/> |always **adEditNone** <br/> |
|[EOF](bof-eof-properties-ado.md) <br/> |read-only  <br/> |
|[Filter](filter-property-ado.md) <br/> |read/write  <br/> |
|[LockType](locktype-property-ado.md) <br/> |read/write  <br/> |
|[MarshalOptions](marshaloptions-property-ado.md) <br/> |not available  <br/> |
|[MaxRecords](maxrecords-property-ado.md) <br/> |read/write  <br/> |
|[PageCount](pagecount-property-ado.md) <br/> |read-only  <br/> |
|[PageSize](pagesize-property-ado.md) <br/> |read/write  <br/> |
|[RecordCount](recordcount-property-ado.md) <br/> |read-only  <br/> |
|[Source](source-property-ado-recordset.md) <br/> |read/write  <br/> |
|[State](state-property-ado.md) <br/> |read-only  <br/> |
|[Status](status-property-ado-recordset.md) <br/> |read-only  <br/> |
   
*Bookmarks must be enabled on the provider in order for this feature to exist on the **Recordset**. 
  
Availability of standard ADO **Recordset** methods: 
  
|**Method**|**Available?**|
|:-----|:-----|
|[AddNew](addnew-method-ado.md) <br/> |No  <br/> |
|[Cancel](cancel-method-ado.md) <br/> |Yes  <br/> |
|[CancelBatch](cancelbatch-method-ado.md) <br/> |No  <br/> |
|[CancelUpdate](cancelupdate-method-ado.md) <br/> |No  <br/> |
|[Clone](clone-method-ado.md) <br/> |Yes  <br/> |
|[Close](close-method-ado.md) <br/> |Yes  <br/> |
|[Delete](delete-method-ado-recordset.md) <br/> |No  <br/> |
|[GetRows](getrows-method-ado.md) <br/> |Yes  <br/> |
|[Move](move-method-ado.md) <br/> |Yes  <br/> |
|[MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) <br/> |Yes  <br/> |
|[NextRecordset](nextrecordset-method-ado.md) <br/> |Yes  <br/> |
|[Open](open-method-ado-recordset.md) <br/> |Yes  <br/> |
|[Requery](requery-method-ado.md) <br/> |Yes  <br/> |
|[Resync](resync-method-ado.md) <br/> |Yes  <br/> |
|[Supports](supports-method-ado.md) <br/> |Yes  <br/> |
|[Update](update-method-ado.md) <br/> |No  <br/> |
|[UpdateBatch](updatebatch-method-ado.md) <br/> |No  <br/> |
   
 **See Also** For specific implementation details and functional information about the Microsoft OLE DB Provider for Microsoft Indexing Service, consult the Microsoft OLE DB Programmer's Reference. 
  

