---
title: 'Step 2: Invoke the Server Program (RDS Tutorial)'
TOCTitle: 'Step 2: Invoke the Server Program (RDS Tutorial)'
ms:assetid: 45429faa-c1e2-d448-a5b4-b2d77cb94377
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249211(v=office.15)
ms:contentKeyID: 48544549
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Step 2: Invoke the Server Program (RDS Tutorial)


_**Applies to:** Access 2013 | Office 2013_

When you invoke a method on the client *proxy*, the actual program on the server executes the method. In this step, you'll execute a query on the server.

**Part A**If you weren't using [RDSServer.DataFactory](datafactory-object-rdsserver.md) in this tutorial, the most convenient way to perform this step would be to use the [RDS.DataControl](datacontrol-object-rds.md) object. The **RDS.DataControl** combines the previous step of creating a proxy, with this step, issuing the query.

Set the **RDS.DataControl** object [Server](server-property-rds.md) property to identify where the server program should be instantiated; the [Connect](connect-property-rds.md) property to specify the connect string to access the data source; and the [SQL](https://msdn.microsoft.com/en-us/library/jj248989\(v=office.15\)) property to specify the query command text. Then issue the [Refresh](refresh-method-rds.md) method to cause the server program to connect to the data source, retrieve rows specified by the query, and return a **Recordset** object to the client.

This tutorial does not use the **RDS.DataControl**, but this is how it would look if it did:

``` 
 
Sub RDSTutorial2A() 
 Dim DC as New RDS.DataControl 
 DC.Server = "http://yourServer" 
 DC.Connect = "DSN=Pubs" 
 DC.SQL = "SELECT * FROM Authors" 
 DC.Refresh 
... 
```

Nor does the tutorial invoke RDS with ADO objects, but this is how it would look if it did:

``` 
 
Dim rs as New ADODB.Recordset 
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" & _ 
"Remote Server=http://yourServer;Remote Provider=SQLOLEDB;" 
```

**Part B**The general method of performing this step is to invoke the **RDSServer.DataFactory** object [Query](query-method-rds.md) method. That method takes a connect string, which is used to connect to a data source, and a command text, which is used to specify the rows to be returned from the data source.

This tutorial uses the **DataFactory** object **Query** method:

``` 
 
Sub RDSTutorial2B() 
 Dim DS as New RDS.DataSpace 
 Dim DF 
 Dim RS as ADODB.Recordset 
 Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer") 
 Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors") 
... 
```

