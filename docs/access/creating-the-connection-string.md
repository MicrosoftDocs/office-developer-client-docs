---
title: "Creating the Connection String"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 0d34b1c6-bf2e-1299-9778-573ccd2da1c7
description: "ADO directly supports five arguments in a connection string. Other arguments are passed to the provider that is named in the Provider argument without any processing by ADO."
---

# Creating the Connection String

ADO directly supports five arguments in a connection string. Other arguments are passed to the provider that is named in the  *Provider*  argument without any processing by ADO. 
  
|**Argument**|**Description**|
|:-----|:-----|
| *Provider*  <br/> |Specifies the name of a provider to use for the connection.  <br/> |
| *File Name*  <br/> |Specifies the name of a provider-specific file (for example, a persisted data source object) containing preset connection information.  <br/> |
| *URL*  <br/> |Specifies the connection string as an absolute URL identifying a resource, such as a file or directory.  <br/> |
| *Remote Provider*  <br/> |Specifies the name of a provider to use when opening a client-side connection. (Remote Data Service only.)  <br/> |
| *Remote Server*  <br/> |Specifies the path name of the server to use when opening a client-side connection. (Remote Data Service only.)  <br/> |
   
> [!NOTE]
> In the following examples and throughout the ADO Programmer's Guide, the user id "MyId" with a password of "123aBc" is used to authenticate against the server. You should substitute these values with valid login credentials for your server. Also, substitute the name of your server for "MySqlServer". 
  
The HelloData application in Chapter 1 used the following connection string:
  
```
 
m_sConnStr = "Provider='SQLOLEDB';Data Source='MySqlServer';" &amp; _ 
 "Initial Catalog='Northwind';Integrated Security='SSPI';" 

```

The only ADO parameter supplied in this connection string was "Provider=SQLOLEDB", which indicated the Microsoft OLE DB Provider for SQL Server. Other valid parameters that can be passed in the connection string can be determined by referring to individual providers' documentation. According to the OLE DB Provider for SQL Server documentation, you can substitute "Server" for the  *Data Source*  parameter and "Database" for the  *Initial Catalog*  parameter. Thus, the following connection string would produce results identical to the first: 
  
```
 
m_sConnStr = "Provider='SQLOLEDB';Server='MySqlServer';" &amp; _ 
 "Database='Northwind';Integrated Security='SSPI';" 

```

To open the connection, simply pass the connection string as the first argument in the **Connection** object **Open** method: 
  
```
 
objConn.Open m_sConnStr 

```

It is also possible to supply much of this information by setting properties of the **Connection** object before opening the connection. For example, you could achieve the same effect as the connection string above by using the following code: 
  
```
 
With objConn 
 .Provider = "SQLOLEDB" 
 .DefaultDatabase = "Northwind" 
 .Properties("Data Source") = "MySqlServer" 
 .Properties("Integrated Security") = "SSPI" 
 .Open 
End With 

```


