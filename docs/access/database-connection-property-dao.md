---
title: "Database.Connection Property (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 8b900ea4-9179-9ed1-bc0b-0576939bb2bd
---

# Database.Connection Property (DAO)

## Syntax

 *expression*  . **Connection**
  
 *expression*  A variable that represents a **Database** object. 
  
## Remarks

Use the **Connection** property to obtain a reference to a **Connection** object that corresponds to the **Database**. In DAO, a **Connection** object and its corresponding **Database** object are simply two different object variable references to the same object. The **[Database](connection-database-property-dao.md)** property of a **Connection** object and the **Connection** property of a **Database** object make it easier to change connections to an ODBC data source through the Microsoft Access database engine to use ODBCDirect. 
  

