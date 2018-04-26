---
title: "Microsoft OLE DB Remoting Provider (ADO Service Provider)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: f39bd83d-8c2c-302e-16e3-0fae50f89fbc
description: "The Microsoft OLE DB Remoting Provider enables a local user on a client machine to invoke data providers on a remote machine. Specify the data provider parameters for the remote machine as you would if you were a local user on the remote machine. Then specify the parameters used by the Remoting Provider to access the remote machine. The resulting effect is that you will access the remote machine as if you were a local user."
---

# Microsoft OLE DB Remoting Provider (ADO Service Provider)

The Microsoft OLE DB Remoting Provider enables a local user on a client machine to invoke data providers on a remote machine. Specify the data provider parameters for the remote machine as you would if you were a local user on the remote machine. Then specify the parameters used by the Remoting Provider to access the remote machine. The resulting effect is that you will access the remote machine as if you were a local user.
  
## Provider Keyword

To invoke the OLE DB Remoting Provider, specify the following keyword and value in the connection string. (Note the blank space in the provider name.)
  
```
 
"Provider=MS Remote" 

```

## Additional Keywords

When this service provider is invoked, the following additional keywords are relevant.
  
|**Keyword**|**Description**|
|:-----|:-----|
|**Data Source** <br/> |Specifies the name of the remote data source. It is passed to the OLE DB Remoting Provider for processing. This keyword is equivalent to the [RDS.DataControl](datacontrol-object-rds.md) object's [Connect](connect-property-rds.md) property.  <br/> |
   
## Dynamic Properties

When this service provider is invoked, the following dynamic properties are added to the [Connection](connection-object-ado.md) object's [Properties](properties-collection-ado.md) collection. 
  
|**Dynamic Property Name**|**Description**|
|:-----|:-----|
|**DFMode** <br/> | Indicates the DataFactory Mode. A string that specifies the desired version of the [DataFactory](datafactory-object-rdsserver.md) object on the server. Set this property before opening a connection to request a particular version of the **DataFactory**. If the requested version is not available, an attempt will be made to use the preceding version. If there is no preceding version, an error will occur. If **DFMode** is less than the available version, an error will occur. This property is read-only after a connection is made. Can be one of the following valid string values:  <br/>  "25" — Version 2.5 (Default)  <br/>  "21" — Version 2.1  <br/>  "20" — Version 2.0  <br/>  "15" — Version 1.5  <br/> |
|**Command Properties** <br/> |Indicates values that will be added to the string of command (rowset) properties sent to the server by the MS Remote provider. The default value for this string is vt_empty.  <br/> |
|**Current DFMode** <br/> | Indicates the actual version number of the **DataFactory** on the server. Check this property to see if the version requested in the **DFMode** property was honored. Can be one of the following valid Long integer values:  <br/>  25 — Version 2.5 (Default)  <br/>  21 — Version 2.1  <br/>  20 — Version 2.0  <br/>  15 — Version 1.5  <br/>  Adding "DFMode=20;" to your connection string when using the **MSRemote** provider can improve your server's performance when updating data. With this setting, the **RDSServer.DataFactory** object on the server uses a less resource-intensive mode. However, the following features are not available in this configuration:  <br/>  Using parameterized queries.  <br/>  Getting parameter or column information before calling the **Execute** method.  <br/>  Setting **Transact Updates** to **True**.  <br/>  Getting row status.  <br/>  Calling the **Resync** method.  <br/>  Refreshing (explicitly or automatically) via the **Update Resync** property.  <br/>  Setting **Command** or **Recordset** properties.  <br/>  Using **adCmdTableDirect**.  <br/> |
|**Handler** <br/> |Indicates the name of a server-side customization program (or handler) that extends the functionality of the [RDSServer.DataFactory](datafactory-object-rdsserver.md), and any parameters used by the handler *,*  all separated by commas (","). A **String** value.  <br/> |
|**Internet Timeout** <br/> |Indicates the maximum number of milliseconds to wait for a request to travel to and from the server. (The default is 5 minutes.)  <br/> |
|**Remote Provider** <br/> |Indicates the name of the data provider to be used on the remote server.  <br/> |
|**Remote Server** <br/> |Indicates the server name and communication protocol to be used by this connection. This property is equivalent to the [RDS.DataControl](datacontrol-object-rds.md) object [Server](server-property-rds.md) property.  <br/> |
|**Transact Updates** <br/> |When set to True, this value indicates that when [UpdateBatch](updatebatch-method-ado.md) is performed on the server, it will be done inside a transaction. The default value for this Boolean dynamic property is False.  <br/> |
   
You may also set writable dynamic properties by specifying their names as keywords in the connection string. For example, set the **Internet Timeout** dynamic property to five seconds by specifying: 
  
```
 
Dim cn as New ADODB.Connection 
cn.Open "Provider=MS Remote;Internet Timeout=5000" 

```

You may also set or retrieve a dynamic property by specifying its name as the index to the **Properties** property. For example, get and print the current value of the **Internet Timeout** dynamic property, and then set a new value, like this: 
  
```
 
Debug.Print cn.Properties("Internet Timeout") 
cn.Properties("Internet Timeout") = 5000 

```

## Remarks

In ADO 2.0, the OLE DB Remoting Provider could only be specified in the  *ActiveConnection*  parameter of the [Recordset](recordset-object-ado.md) object **Open** method. Starting with ADO 2.1, the provider may also be specified in the  *ConnectionString*  parameter of the [Connection](connection-object-ado.md) object **Open** method. 
  
The equivalent of the **RDS.DataControl** object [SQL](http://msdn.microsoft.com/library/210adcbb-5c89-150b-4c61-6a52dea9af56%28Office.15%29.aspx) property is not available. The [Recordset](recordset-object-ado.md) object **Open** method  *Source*  argument is used instead. 
  
Specifying "...;Remote Provider=MS Remote;..." would create a four-tier scenario.Scenarios beyond three tiers have not been tested and should not be needed.
  
## Example

This example performs a query on the **authors** table of the **pubs** database on a server named,  *YourServer*  . The names of the remote data source and remote server are provided in the [Connection](connection-object-ado.md) object [Open](open-method-ado-connection.md) method, and the SQL query is specified in the [Recordset](recordset-object-ado.md) object [Open](open-method-ado-recordset.md) method. A **Recordset** object is returned, edited, and used to update the data source. 
  
```
 
Dim rs as New ADODB.Recordset 
Dim cn as New ADODB.Connection 
cn.Open  "Provider=MS Remote;Data Source=pubs;" &amp; _ 
         "Remote Server=http://YourServer" 
rs.Open "SELECT * FROM authors", cn 
...                'Edit the recordset 
rs.UpdateBatch     'Equivalent of RDS SubmitChanges 
... 

```


