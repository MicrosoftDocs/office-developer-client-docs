---
title: "Service Providers and Components"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e42d9c84-525a-4aca-01b2-88e3f2b0717f
description: "Service providers are components that extend the functionality of data providers by implementing extended interfaces that are not natively supported by the data store."
---

# Service Providers and Components

Service providers are components that extend the functionality of data providers by implementing extended interfaces that are not natively supported by the data store.
  
Microsoft Data Access provides a  *component architecture*  that allows individual, specialized components to implement discrete sets of database functionality, or "services," on top of less capable stores. Thus, rather than forcing each data store to provide its own implementation of extended functionality or forcing generic applications to implement database functionality internally, service components provide a common implementation that any application can use when accessing any data store. The fact that some functionality is implemented natively by the data store and some through generic components is transparent to the application. 
  
For example, a cursor engine, such as the Microsoft Cursor Service for OLE DB, is a service component that can consume data from a sequential, forward-only data store to produce scrollable data. Other service providers commonly used by ADO include the Microsoft OLE DB Persistence Provider (for saving data to a file), the Microsoft Data Shaping Service for OLE DB (for hierarchical **Recordsets** ), and the Microsoft OLE DB Remoting Provider (for invoking data providers on a remote computer). 
  
For more information about service and data providers, see [Appendix A: Providers](appendix-a-providers.md).
  

