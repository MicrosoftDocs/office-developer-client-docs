---
title: "Microsoft OLE DB Provider for Microsoft Active Directory Service"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 92d1c967-aa61-f3b5-1c0a-301ef236894c

description: "The Microsoft Active Directory Service Interfaces (ADSI) Provider allows ADO to connect to heterogeneous directory services through ADSI. This gives ADO applications read-only access to the Microsoft Windows NT 4.0 and Microsoft Windows 2000 directory services, in addition to any LDAP-compliant directory service and Novell Directory Services. ADSI itself is based on a provider model, so if there is a new provider giving access to another directory, the ADO application will be able to access it seamlessly. The ADSI provider is free-threaded and unicode enabled."
---

# Microsoft OLE DB Provider for Microsoft Active Directory Service

The Microsoft Active Directory Service Interfaces (ADSI) Provider allows ADO to connect to heterogeneous directory services through ADSI. This gives ADO applications read-only access to the Microsoft Windows NT 4.0 and Microsoft Windows 2000 directory services, in addition to any LDAP-compliant directory service and Novell Directory Services. ADSI itself is based on a provider model, so if there is a new provider giving access to another directory, the ADO application will be able to access it seamlessly. The ADSI provider is free-threaded and unicode enabled.
  
## Connection String Parameters

To connect to this provider, set the **Provider** argument of the [ConnectionString](connectionstring-property-ado.md) property to: 
  
```
 
ADSDSOObject 

```

Reading the [Provider](provider-property-ado.md) property will return this string as well. 
  
## Typical Connection String

A typical connection string for this provider is:
  
```
 
"Provider=ADSDSOObject;User ID=userName ;Password=userPassword ;" 

```

The string consists of these keywords:
  
|**Keyword**|**Description**|
|:-----|:-----|
|**Provider** <br/> |Specifies the OLE DB Provider for Microsoft Active Directory Service.  <br/> |
|**User ID** <br/> |Specifies the user name. If this keyword is omitted, then the current logon is used.  <br/> |
|**Password** <br/> |Specifies the user password. If this keyword is omitted, then the current logon is used.  <br/> |
   
 **Command Text**
  
A four-part command text string is recognized by the provider in the following syntax:
  
```
"Root;Filter;Attributes [;Scope ]"
```

|**Value**|**Description**|
|:-----|:-----|
| *Root*  <br/> |Indicates the **ADsPath** object from which to start the search (that is, the root of the search).  <br/> |
| *Filter*  <br/> |Indicates the search filter in the RFC 1960 format.  <br/> |
| *Attributes*  <br/> |Indicates a comma-delimited list of attributes to be returned.  <br/> |
| *Scope*  <br/> |Optional. A **String** that specifies the scope of the search. Can be one of the following: Base — Search only the base object (root of the search).           OneLevel — Search only one level.          Subtree — Search the entire subtree.  <br/> |
   
For example:
  
```
 
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree" 

```

The provider also supports SQL SELECT for command text. For example:
  
```
 
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE 
objectClass='user' AND objectCategory='Person'" 

```

The provider does not accept stored procedure calls or simple table names (for example, the [CommandType](commandtype-property-ado.md) property will always be **adCmdText** ). See the Active Directory Service Interfaces documentation for a more complete description of the command text elements. 
  
## Recordset Behavior

The following tables list the features available on a [Recordset](recordset-object-ado.md) object opened with this provider. Only the Static cursor type ( **adOpenStatic** ) is available. 
  
For more detailed information about **Recordset** behavior for your provider configuration, run the [Supports](supports-method-ado.md) method and enumerate the [Properties](properties-collection-ado.md) collection of the **Recordset** to determine whether provider-specific dynamic properties are present. 
  
Availability of standard ADO **Recordset** properties: 
  
|**Property**|**Availability**|
|:-----|:-----|
|[AbsolutePage](absolutepage-property-ado.md) <br/> |read/write  <br/> |
|[AbsolutePosition](absoluteposition-property-ado.md) <br/> |read/write  <br/> |
|[ActiveConnection](activeconnection-property-ado.md) <br/> |read-only  <br/> |
|[BOF](bof-eof-properties-ado.md) <br/> |read-only  <br/> |
|[Bookmark](bookmark-property-ado.md) <br/> |read/write  <br/> |
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
   
Availability of standard ADO **Recordset** methods: 
  
|**Method**|**Available?**|
|:-----|:-----|
|[AddNew](addnew-method-ado.md) <br/> |No  <br/> |
|[Cancel](cancel-method-ado.md) <br/> |No  <br/> |
|[CancelBatch](cancelbatch-method-ado.md) <br/> |No  <br/> |
|[CancelUpdate](cancelupdate-method-ado.md) <br/> |No  <br/> |
|[Clone](clone-method-ado.md) <br/> |Yes  <br/> |
|[Close](close-method-ado.md) <br/> |Yes  <br/> |
|[Delete](delete-method-ado-recordset.md) <br/> |No  <br/> |
|[GetRows](getrows-method-ado.md) <br/> |Yes  <br/> |
|[Move](move-method-ado.md) <br/> |Yes  <br/> |
|[MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) <br/> |Yes  <br/> |
|[MoveLast](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) <br/> |Yes  <br/> |
|[MoveNext](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) <br/> |Yes  <br/> |
|[MovePrevious](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) <br/> |Yes  <br/> |
|[NextRecordset](nextrecordset-method-ado.md) <br/> |Yes  <br/> |
|[Open](open-method-ado-recordset.md) <br/> |Yes  <br/> |
|[Requery](requery-method-ado.md) <br/> |Yes  <br/> |
|[Resync](resync-method-ado.md) <br/> |Yes  <br/> |
|[Supports](supports-method-ado.md) <br/> |Yes  <br/> |
|[Update](update-method-ado.md) <br/> |No  <br/> |
|[UpdateBatch](updatebatch-method-ado.md) <br/> |No  <br/> |
   

