---
title: "Connection Object (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: f469b04e-2539-6b53-31f2-85fe22fcc2fc
description: "A Connection object represents a connection to an ODBC database (ODBCDirect workspaces only)."
---

# Connection Object (DAO)

> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
A **Connection** object represents a connection to an ODBC database (ODBCDirect workspaces only). 
  
## Remarks

A **Connection** is a non-persistent object that represents a connection to a remote database. The **Connection** object is only available in ODBCDirect workspaces (that is, a **Workspace** object created with the type option set to **dbUseODBC** ). 
  
> [!NOTE]
> Code written for earlier versions of DAO can continue to use the **Database** object for backward compatibility, but if the new features of a **Connection** are desired, you should revise code to use the **Connection** object. To help with code conversion, you can obtain a **Connection** object reference from a **Database** by reading the [Connection](database-connection-property-dao.md) property of the **Database** object. Conversely, you can obtain a **Database** object reference from the **Connection** object's **Database** property. 
  

