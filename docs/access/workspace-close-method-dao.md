---
title: "Workspace.Close Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 9b3d28f9-5cde-0dd9-8a4a-d2efaec5fe5d
description: "Closes an open Workspace ."
---

# Workspace.Close Method (DAO)

Closes an open **Workspace**. 
  
## Syntax

 *expression*  . **Close**
  
 *expression*  A variable that represents a **Workspace** object. 
  
## Remarks

If the **Workspace** object is already closed when you use **Close**, a run-time error occurs. 
  
An alternative to the **Close** method is to set the value of an object variable to **Nothing** (  `Set dbsTemp = Nothing`).
  

