---
title: Making a Connection
TOCTitle: Making a Connection
ms:assetid: 188f6794-f4ec-8e8d-5adc-bdee36f4c9ae
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ248932(v=office.15)
ms:contentKeyID: 48543472
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Making a Connection


_**Applies to:** Access 2013 | Office 2013_

To connect to a data source, you must specify a *connection string*, the parameters of which might differ for each provider and data source. For more information, see [Creating the Connection String](creating-the-connection-string.md).

ADO most commonly opens a connection by using the **Connection** object **Open** method. The syntax for the **Open** method is shown here:

``` 
 
Dim connection as New ADODB.Connection 
connection.Open ConnectionString, UserID, Password, OpenOptions
```

Alternatively, you can invoke a shortcut technique, **Recordset.Open**, to open an implicit connection and issue a command over that connection in one operation. Do this by passing in a valid connection string as the *ActiveConnection* argument to the **Open** method. Here is the syntax for each method in Visual Basic:

``` 
 
Dim recordset as ADODB.Recordset 
Set recordset = New ADODB.Recordset 
recordset.Open Source, ActiveConnection, CursorType, LockType, Options
```


> [!NOTE]
> <P>When should you use a <STRONG>Connection</STRONG> object vs. the <STRONG>Recordset.Open</STRONG> shortcut? Use the <STRONG>Connection</STRONG> object if you plan to open more than one <STRONG>Recordset</STRONG>, or when executing multiple commands. A connection is still created by ADO implicitly when you use the <STRONG>Recordset.Open</STRONG> shortcut.</P>


