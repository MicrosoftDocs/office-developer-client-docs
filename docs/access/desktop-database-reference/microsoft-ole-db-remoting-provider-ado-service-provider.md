---
title: Microsoft OLE DB Remoting Provider (ADO Service Provider)
TOCTitle: Microsoft OLE DB Remoting Provider (ADO Service Provider)
ms:assetid: f39bd83d-8c2c-302e-16e3-0fae50f89fbc
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250238(v=office.15)
ms:contentKeyID: 48548673
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Microsoft OLE DB Remoting Provider (ADO Service Provider)

**Applies to**: Access 2013, Office 2013

The Microsoft OLE DB Remoting Provider enables a local user on a client machine to invoke data providers on a remote machine. Specify the data provider parameters for the remote machine as you would if you were a local user on the remote machine. Then specify the parameters used by the Remoting Provider to access the remote machine. The resulting effect is that you will access the remote machine as if you were a local user.

## Provider Keyword

To invoke the OLE DB Remoting Provider, specify the following keyword and value in the connection string. (Note the blank space in the provider name.)

```sql 
 
"Provider=MS Remote" 
```

## Additional Keywords

When this service provider is invoked, the following additional keywords are relevant.

<table>
<colgroup>
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Data Source</strong></p></td>
<td><p>Specifies the name of the remote data source. It is passed to the OLE DB Remoting Provider for processing. This keyword is equivalent to the <a href="datacontrol-object-rds.md">RDS.DataControl</a> object's <a href="connect-property-rds.md">Connect</a> property.</p></td>
</tr>
</tbody>
</table>


## Dynamic Properties

When this service provider is invoked, the following dynamic properties are added to the [Connection](connection-object-ado.md) object's [Properties](properties-collection-ado.md) collection.

<table>
<colgroup>
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Dynamic Property Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>DFMode</strong></p></td>
<td><p>Indicates the DataFactory Mode. A string that specifies the desired version of the <a href="datafactory-object-rdsserver.md">DataFactory</a> object on the server. Set this property before opening a connection to request a particular version of the <strong>DataFactory</strong>. If the requested version is not available, an attempt will be made to use the preceding version. If there is no preceding version, an error will occur. If <strong>DFMode</strong> is less than the available version, an error will occur. This property is read-only after a connection is made. Can be one of the following valid string values:</p>
<p></p>
<ul>
<li><p>&quot;25&quot; — Version 2.5 (Default)</p></li>
<li><p>&quot;21&quot; — Version 2.1</p></li>
<li><p>&quot;20&quot; — Version 2.0</p></li>
<li><p>&quot;15&quot; — Version 1.5</p></li>
</ul>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>Command Properties</strong></p></td>
<td><p>Indicates values that will be added to the string of command (rowset) properties sent to the server by the MS Remote provider. The default value for this string is vt_empty.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Current DFMode</strong></p></td>
<td><p>Indicates the actual version number of the <strong>DataFactory</strong> on the server. Check this property to see if the version requested in the <strong>DFMode</strong> property was honored. Can be one of the following valid Long integer values:</p>
<p></p>
<ul>
<li><p>25 — Version 2.5 (Default)</p></li>
<li><p>21 — Version 2.1</p></li>
<li><p>20 — Version 2.0</p></li>
<li><p>15 — Version 1.5</p></li>
</ul>
<p></p>
<p>Adding &quot;DFMode=20;&quot; to your connection string when using the <strong>MSRemote</strong> provider can improve your server's performance when updating data. With this setting, the <strong>RDSServer.DataFactory</strong> object on the server uses a less resource-intensive mode. However, the following features are not available in this configuration:</p>
<p></p>
<ul>
<li><p>Using parameterized queries.</p></li>
<li><p>Getting parameter or column information before calling the <strong>Execute</strong> method.</p></li>
<li><p>Setting <strong>Transact Updates</strong> to <strong>True</strong>.</p></li>
<li><p>Getting row status.</p></li>
<li><p>Calling the <strong>Resync</strong> method.</p></li>
<li><p>Refreshing (explicitly or automatically) via the <strong>Update Resync</strong> property.</p></li>
<li><p>Setting <strong>Command</strong> or <strong>Recordset</strong> properties.</p></li>
<li><p>Using <strong>adCmdTableDirect</strong>.</p></li>
</ul>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>Handler</strong></p></td>
<td><p>Indicates the name of a server-side customization program (or handler) that extends the functionality of the <a href="datafactory-object-rdsserver.md">RDSServer.DataFactory</a>, and any parameters used by the handler<em>,</em> all separated by commas (&quot;,&quot;). A <strong>String</strong> value.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Internet Timeout</strong></p></td>
<td><p>Indicates the maximum number of milliseconds to wait for a request to travel to and from the server. (The default is 5 minutes.)</p></td>
</tr>
<tr class="even">
<td><p><strong>Remote Provider</strong></p></td>
<td><p>Indicates the name of the data provider to be used on the remote server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Remote Server</strong></p></td>
<td><p>Indicates the server name and communication protocol to be used by this connection. This property is equivalent to the <a href="datacontrol-object-rds.md">RDS.DataControl</a> object <a href="server-property-rds.md">Server</a> property.</p></td>
</tr>
<tr class="even">
<td><p><strong>Transact Updates</strong></p></td>
<td><p>When set to True, this value indicates that when <a href="updatebatch-method-ado.md">UpdateBatch</a> is performed on the server, it will be done inside a transaction. The default value for this Boolean dynamic property is False.</p></td>
</tr>
</tbody>
</table>


You may also set writable dynamic properties by specifying their names as keywords in the connection string. For example, set the **Internet Timeout** dynamic property to five seconds by specifying:

```sql 
 
Dim cn as New ADODB.Connection 
cn.Open "Provider=MS Remote;Internet Timeout=5000" 
```

You may also set or retrieve a dynamic property by specifying its name as the index to the **Properties** property. For example, get and print the current value of the **Internet Timeout** dynamic property, and then set a new value, like this:

```sql 
 
Debug.Print cn.Properties("Internet Timeout") 
cn.Properties("Internet Timeout") = 5000 
```

## Remarks

In ADO 2.0, the OLE DB Remoting Provider could only be specified in the *ActiveConnection* parameter of the [Recordset](recordset-object-ado.md) object **Open** method. Starting with ADO 2.1, the provider may also be specified in the *ConnectionString* parameter of the [Connection](connection-object-ado.md) object **Open** method.

The equivalent of the **RDS.DataControl** object [SQL](/office/vba/access/concepts/miscellaneous/sql-property-ado) property is not available. The [Recordset](recordset-object-ado.md) object **Open** method *Source* argument is used instead.

Specifying "...;Remote Provider=MS Remote;..." would create a four-tier scenario.Scenarios beyond three tiers have not been tested and should not be needed.

## Example

This example performs a query on the **authors** table of the **pubs** database on a server named, *YourServer*. The names of the remote data source and remote server are provided in the [Connection](connection-object-ado.md) object [Open](open-method-ado-connection.md) method, and the SQL query is specified in the [Recordset](recordset-object-ado.md) object [Open](open-method-ado-recordset.md) method. A **Recordset** object is returned, edited, and used to update the data source.

```vb 
 
Dim rs as New ADODB.Recordset 
Dim cn as New ADODB.Connection 
cn.Open  "Provider=MS Remote;Data Source=pubs;" & _ 
         "Remote Server=https://YourServer" 
rs.Open "SELECT * FROM authors", cn 
...                'Edit the recordset 
rs.UpdateBatch     'Equivalent of RDS SubmitChanges 
... 
```

