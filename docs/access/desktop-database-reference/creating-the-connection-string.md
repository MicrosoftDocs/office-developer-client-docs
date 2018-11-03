---
title: Creating the connection string
TOCTitle: Creating the connection string
ms:assetid: 0d34b1c6-bf2e-1299-9778-573ccd2da1c7
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248853(v=office.15)
ms:contentKeyID: 48543214
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Creating the connection string

**Applies to**: Access 2013, Office 2013

ADO directly supports five arguments in a connection string. Other arguments are passed to the provider that is named in the *Provider* argument without any processing by ADO.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Provider</em></p></td>
<td><p>Specifies the name of a provider to use for the connection.</p></td>
</tr>
<tr class="even">
<td><p><em>File Name</em></p></td>
<td><p>Specifies the name of a provider-specific file (for example, a persisted data source object) containing preset connection information.</p></td>
</tr>
<tr class="odd">
<td><p><em>URL</em></p></td>
<td><p>Specifies the connection string as an absolute URL identifying a resource, such as a file or directory.</p></td>
</tr>
<tr class="even">
<td><p><em>Remote Provider</em></p></td>
<td><p>Specifies the name of a provider to use when opening a client-side connection. (Remote Data Service only.)</p></td>
</tr>
<tr class="odd">
<td><p><em>Remote Server</em></p></td>
<td><p>Specifies the path name of the server to use when opening a client-side connection. (Remote Data Service only.)</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> In the following examples and throughout the ADO programmer's guide, the user id "MyId" with a password of "123aBc" is used to authenticate against the server. You should substitute these values with valid login credentials for your server. Also, substitute the name of your server for "MySqlServer".

The HelloData application in Chapter 1 used the following connection string:

```vb 
 
m_sConnStr = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _ 
 "Initial Catalog='Northwind';Integrated Security='SSPI';" 
```

The only ADO parameter supplied in this connection string was "Provider=SQLOLEDB", which indicated the Microsoft OLE DB Provider for SQL Server. Other valid parameters that can be passed in the connection string can be determined by referring to individual providers' documentation. According to the OLE DB Provider for SQL Server documentation, you can substitute "Server" for the *Data Source* parameter and "Database" for the *Initial Catalog* parameter. Thus, the following connection string would produce results identical to the first:

```vb 
 
m_sConnStr = "Provider='SQLOLEDB';Server='MySqlServer';" & _ 
 "Database='Northwind';Integrated Security='SSPI';" 
```

To open the connection, simply pass the connection string as the first argument in the **Connection** object **Open** method:

```vb 
 
objConn.Open m_sConnStr 
```

It is also possible to supply much of this information by setting properties of the **Connection** object before opening the connection. For example, you could achieve the same effect as the connection string above by using the following code:

```vb 
 
With objConn 
 .Provider = "SQLOLEDB" 
 .DefaultDatabase = "Northwind" 
 .Properties("Data Source") = "MySqlServer" 
 .Properties("Integrated Security") = "SSPI" 
 .Open 
End With 
```

