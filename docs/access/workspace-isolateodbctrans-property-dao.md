---
title: "Workspace.IsolateODBCTrans Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1053083
  
localization_priority: Normal
ms.assetid: f7a48358-870b-cad3-d4ef-e46b50428e12
description: "Sets or returns a value that indicates whether multiple transactiond that involve the same Microsoft Access database engine-connected ODBC data source are isolated (Microsoft Access workspaces only)."
---

# Workspace.IsolateODBCTrans Property (DAO)

Sets or returns a value that indicates whether multiple transactiond that involve the same Microsoft Access database engine-connected ODBC data source are isolated (Microsoft Access workspaces only).
  
## Syntax

 *expression*  . **IsolateODBCTrans**
  
 *expression*  A variable that represents a **Workspace** object. 
  
## Remarks

In some situations, you need to have multiple simultaneous transactions pending on the same ODBC connection. To do this, you need to open a separate **Workspace** for each transaction. Although each **Workspace** can have its own ODBC connection to the database, this slows system performance. Because transaction isolation isn't usually required, ODBC connections from multiple **Workspace** objects opened by the same user are shared by default. 
  
Some ODBC servers, such as Microsoft SQL Server, don't allow simultaneous transactions on a single connection. If you need to have more than one transaction at a time pending against such a database, set the **IsolateODBCTrans** property to **True** on each **Workspace** as soon as you open it. This forces a separate ODBC connection for each **Workspace**. 
  

