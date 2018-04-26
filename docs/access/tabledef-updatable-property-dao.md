---
title: "TableDef.Updatable Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 0b1ae7e5-416d-06f0-5d74-989c6db67ff2
description: "Returns a value that indicates whether you can change a DAO object. Read-only Boolean ."
---

# TableDef.Updatable Property (DAO)

Returns a value that indicates whether you can change a DAO object. Read-only **Boolean**. 
  
## Syntax

 *expression*  . **Updatable**
  
 *expression*  A variable that represents a **TableDef** object. 
  
## Remarks

The **Updatable** property setting is always **True** for a newly created **TableDef** object and **False** for a linked **TableDef** object. A new **TableDef** object can be appended only to a database for which the current user has write permission. 
  

