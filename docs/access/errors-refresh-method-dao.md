---
title: "Errors.Refresh Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: dc352c5f-09d0-bfb3-b24a-4c3454dbf5aa
description: "Updates the objects in the specified colletion to reflect the database's current schema."
---

# Errors.Refresh Method (DAO)

Updates the objects in the specified colletion to reflect the database's current schema.
  
## Syntax

 *expression*  . **Refresh**
  
 *expression*  A variable that represents an **Errors** object. 
  
## Remarks

Use the **Refresh** method in multiuser environments in which other users may change the database. You may also need to use it on any collections that are indirectly affected by changes to the database. For example, if you change a **Users** collection, you may need to refresh a **Groups** collection before using the **Groups** collection. 
  
A collection is filled with objects the first time it's referred to and won't automatically reflect subsequent changes other users make. If it's likely that another user has changed a collection, use the Refresh method on the collection immediately before carrying out any task in your application that assumes the presence or absence of a particular object in the collection. This will ensure that the collection is as up-to-date as possible. On the other hand, using Refresh can unnecessarily slow performance.
  

