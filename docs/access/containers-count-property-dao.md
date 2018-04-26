---
title: "Containers.Count Property (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 3b0bf865-a4d5-82bb-c1a9-9957f110db4c
description: "Returns the number of Connection objects in the Connections collection."
---

# Containers.Count Property (DAO)

Returns the number of **[Connection](connection-object-dao.md)** objects in the **[Connections](connections-collection-dao.md)** collection. 
  
## Syntax

 *expression*  . **Count**
  
 *expression*  A variable that represents a **Connections** object. 
  
## Remarks

Because members of a collection begin with 0, you should always code loops starting with the 0 member and ending with the value of the **Count** property minus 1. If you want to loop through the members of a collection without checking the **Count** property, you can use a **For Each...Next** command. 
  
The **Count** property setting is never Null. If its value is 0, there are no objects in the collection. 
  

