---
title: Using the Connection Object (Access)
TOCTitle: Using the Connection Object
ms:assetid: e8786411-2be4-8d75-9df7-e345d5a6a7e8
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250177(v=office.15)
ms:contentKeyID: 48548423
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Using the Connection Object (Access)


**Applies to**: Access 2013 | Office 2013

A **Connection** object represents a unique session with a data source. In the case of a client/server database system, it can be equivalent to an actual network connection to the server. Depending on the functionality supported by the provider, some collections, methods, or properties of a **Connection** object might not be available.

Before opening a **Connection** object, you must define certain information about the data source and type of connection. The *ConnectionString* parameter of the **Connection** object **Open** method — or the **ConnectionString** property on the **Connection** object — usually contains most of this information. A connection string is a string of characters that defines a variable number of arguments. The arguments — some required by ADO, but others provider-specific — contain information that the **Connection** object must have to carry out its work. The arguments that make up the *ConnectionString* parameter are separated with semicolons (;).


> [!NOTE]
> <P>You can also specify an ODBC Data Source Name (DSN) or a Data Link (UDL) file in a connection string. For more information about DSNs, see Data Sources in Part 1 of the <EM>ODBC Programmer's Reference</EM>. For more information about UDLs, see Data Link API Overview in the <EM>OLE DB Programmer's Reference</EM>.</P>


