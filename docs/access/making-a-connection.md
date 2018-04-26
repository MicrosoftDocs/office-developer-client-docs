---
title: "Making a Connection"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 188f6794-f4ec-8e8d-5adc-bdee36f4c9ae
description: "To connect to a data source, you must specify a connection string , the parameters of which might differ for each provider and data source. For more information, see Creating the Connection String."
---

# Making a Connection

To connect to a data source, you must specify a  *connection string*  , the parameters of which might differ for each provider and data source. For more information, see [Creating the Connection String](creating-the-connection-string.md).
  
ADO most commonly opens a connection by using the **Connection** object **Open** method. The syntax for the **Open** method is shown here: 
  
```
 
Dim connection as New ADODB.Connection 
connection.OpenConnectionString , UserID , Password , OpenOptions
```

Alternatively, you can invoke a shortcut technique, **Recordset.Open**, to open an implicit connection and issue a command over that connection in one operation. Do this by passing in a valid connection string as the  *ActiveConnection*  argument to the **Open** method. Here is the syntax for each method in Visual Basic: 
  
```
 
Dim recordset as ADODB.Recordset 
Set recordset = New ADODB.Recordset 
recordset.OpenSource , ActiveConnection , CursorType , LockType , Options
```

> [!NOTE]
> When should you use a **Connection** object vs. the **Recordset.Open** shortcut? Use the **Connection** object if you plan to open more than one **Recordset**, or when executing multiple commands. A connection is still created by ADO implicitly when you use the **Recordset.Open** shortcut. 
  

