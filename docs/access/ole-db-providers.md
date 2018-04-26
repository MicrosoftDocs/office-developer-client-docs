---
title: "OLE DB Providers"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ef412198-eac5-bf86-73fd-574e67276408
description: "The ADO Programmer's Guide Introduction discusses the relationship between ADO and the rest of the Microsoft Data Access architecture. OLE DB defines a set of COM interfaces to provide applications with uniform access to data that is stored in diverse information sources. This approach allows a data source to share its data through the interfaces that support the amount of DBMS functionality appropriate to the data source. By design, the high-performance architecture of OLE DB is based on its use of a flexible, component-based services model. Rather than having a prescribed number of intermediary layers between the application and the data, OLE DB requires only as many components as are needed to accomplish a particular task."
---

# OLE DB Providers

The ADO Programmer's Guide [Introduction](introduction-to-ado-programming.md) discusses the relationship between ADO and the rest of the Microsoft Data Access architecture. OLE DB defines a set of COM interfaces to provide applications with uniform access to data that is stored in diverse information sources. This approach allows a data source to share its data through the interfaces that support the amount of DBMS functionality appropriate to the data source. By design, the high-performance architecture of OLE DB is based on its use of a flexible, component-based services model. Rather than having a prescribed number of intermediary layers between the application and the data, OLE DB requires only as many components as are needed to accomplish a particular task. 
  
For example, suppose a user wants to run a query. Consider the following scenarios:
  
- The data resides in a relational database for which there currently exists an ODBC driver but no native OLE DB provider: The application uses ADO to talk to the OLE DB Provider for ODBC, which then loads the appropriate ODBC driver. The driver passes the SQL statement to the DBMS, which retrieves the data.
    
- The data resides in Microsoft SQL Server for which there is a native OLE DB provider: The application uses ADO to talk directly to the OLE DB Provider for Microsoft SQL Server. No intermediaries are required.
    
- The data resides in Microsoft Exchange Server, for which there is an OLE DB provider but which does not expose an engine to process SQL queries: The application uses ADO to talk to the OLE DB Provider for Microsoft Exchange and calls upon an OLE DB query processor component to handle the querying.
    
- The data resides in the Microsoft NTFS file system in the form of documents: Data is accessed by using a native OLE DB provider over Microsoft Indexing Service, which indexes the content and properties of documents in the file system to enable efficient content searches.
    
In all of the preceding examples, the application can query the data. The user's needs are met with a minimum number of components. In each case, additional components are used only if needed, and only the required components are invoked. This demand-loading of reusable and shareable components greatly contributes to high performance when OLE DB is used.
  
Providers fall into two categories: those providing data and those providing services. A [data provider](data-providers.md) owns its own data and exposes it in tabular form to your application. A [service provider](service-providers-and-components.md) encapsulates a service by producing and consuming data, augmenting features in your ADO applications. A service provider may also be further defined as a [service component](service-providers-and-components.md), which must work in conjunction with other service providers or components.
  
ADO provides a consistent, higher level interface to the various OLE DB providers.
  

