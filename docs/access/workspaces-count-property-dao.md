---
title: "Workspaces.Count Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: bc7c5a11-13d3-27bd-1be4-5d069e888ac2
description: "Returns the number of objects in the specified collection. Read-only."
---

# Workspaces.Count Property (DAO)

Returns the number of objects in the specified collection. Read-only.
  
## Syntax

 *expression*  . **Count**
  
 *expression*  A variable that represents a **Workspaces** object. 
  
## Remarks

Because members of a collection begin with 0, you should always code loops starting with the 0 member and ending with the value of the **Count** property minus 1. If you want to loop through the members of a collection without checking the **Count** property, you can use a **For Each...Next** command. 
  
The **Count** property setting is never Null. If its value is 0, there are no objects in the collection. 
  

