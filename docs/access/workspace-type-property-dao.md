---
title: "Workspace.Type Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 89e59280-d2cd-b6a2-16c5-9f14f42fdd99
description: "Sets or returns a value that indicates the operational type or data type of an object. Read-only Integer ."
---

# Workspace.Type Property (DAO)

Sets or returns a value that indicates the operational type or data type of an object. Read-only **Integer**. 
  
## Syntax

 *expression*  . **Type**
  
 *expression*  A variable that represents a **Workspace** object. 
  
## Remarks

For a **Workspace** object, the possible settings and return values are as follows. 
  
|**Constant**|**Workspace type**|
|:-----|:-----|
|**dbUseJet** <br/> |The **Workspace** is connected to the Microsoft Access database engine.  <br/> |
|**dbUseODBC** <br/> |The **Workspace** is connected to an ODBC data source.  <br/> |
   

