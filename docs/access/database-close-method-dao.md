---
title: "Database.Close Method (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: b777ee92-172a-3342-31fc-76e7361c47fd
description: "Closes an open Database ."
---

# Database.Close Method (DAO)

Closes an open **Database**. 
  
## Syntax

 *expression*  . **Close**
  
 *expression*  A variable that represents a **Database** object. 
  
## Remarks

If the **Database** object is already closed when you use **Close**, a run-time error occurs. 
  
An alternative to the **Close** method is to set the value of an object variable to **Nothing** (  `Set dbsTemp = Nothing`).
  

