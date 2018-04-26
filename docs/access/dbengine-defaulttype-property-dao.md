---
title: "DBEngine.DefaultType Property (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- dao360.chm1053580
  
localization_priority: Normal
ms.assetid: b4371f3e-1ce0-1d0f-93a8-0c5329b510ab
description: "Sets or returns a value that indicates what type of workspace will be used by the next Workspace object created."
---

# DBEngine.DefaultType Property (DAO)

Sets or returns a value that indicates what type of workspace will be used by the next **[Workspace](workspace-object-dao.md)** object created. 
  
## Syntax

 *expression*  . **DefaultType**
  
 *expression*  A variable that represents a **DBEngine** object. 
  
## Remarks

The setting or return value can be one of the of the **[WorkspaceTypeEnum](workspacetypeenum-enumeration-dao.md)** constants. 
  
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
The setting can be overridden for a single **Workspace** by setting the  _type_ argument to the **[CreateWorkspace](dbengine-createworkspace-method-dao.md)** method. 
  

