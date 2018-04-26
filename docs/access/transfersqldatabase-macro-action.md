---
title: "TransferSQLDatabase Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm111536
  
localization_priority: Normal
ms.assetid: 8cb95e22-f1f0-6c70-7dcb-3a3e9aafdc57
description: "In an Access project, you can use the TransferSQLDatabase action to transfer a Microsoft SQL Server 7.0 or later database to another SQL Server 7.0 or later database. For more information on transferring a database, see the SQL Server documentation."
---

# TransferSQLDatabase Macro Action

In an Access project, you can use the **TransferSQLDatabase** action to transfer a Microsoft SQL Server 7.0 or later database to another SQL Server 7.0 or later database. For more information on transferring a database, see the SQL Server documentation. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **TransferSQLDatabase** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Server** <br/> |The name of the SQL Server 7.0 or later database server you are copying to.  <br/> |
|**Database** <br/> |The name of the new database that will be created on the destination server.  <br/> |
|**Use Trusted Connection** <br/> |Specifes whether or not there is a trusted connection to the SQL Server. If set to **Yes**, then there is a trusted connection and the **Login** and **Password** arguments are not required. If set to **No**, the **Login** and **Password** arguments are required. The default is **Yes**. When you use a trusted connection, SQL Server security integrates with the Windows operating system security to provide a single log on to the network and the database.  <br/> |
|**Login** <br/> |The name of the Login to the destination server.  <br/> |
|**Password** <br/> |The password for the **Login** argument. This password is stored as text in the Access project, but is hidden during the transfer database operation.  <br/> |
|**Transfer Copy Data** <br/> |Specifies whether or not to include data in the transfer database operation. When set to **Yes**, all data is included for all the tables, along with all data structures, extended properties, and database objects. When set to **No**, no data is included from the tables. Only the table structure and extended properties are created on the destination server, along with all other database objects (except database diagrams). The default is **Yes**.  <br/> |
   
## Remarks

You cannot perform other operations while the database is being transferred.
  
The **TransferSQLDatabase** action, by default, copies data, data definitions, database objects, and extended properties, such as default values, text constraints, and lookup values. 
  
There are requirements for transferring a database:
  
- You must be a member of the sysadmin role on the destination server (No special role is required on the source server).
    
- The current SQL server connected to the Access project and the destination server you are transferring the database to must be SQL Server version 7.0 or later.
    
> [!NOTE]
> Linked servers are not transferred during a database transfer operation. 
  
To run the **TransferSQLDatabase** action in a Visual Basic for Applications (VBA) module, use the **TransferSQLDatabase** method of the **DoCmd** object. 
  

