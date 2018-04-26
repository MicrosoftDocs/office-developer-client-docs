---
title: "Recordset.Updatable Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 2d4bdcef-1b10-b542-ce0f-6172c271131b
description: "Returns a value that indicates whether you can change a DAO object. Read-only Boolean ."
---

# Recordset.Updatable Property (DAO)

Returns a value that indicates whether you can change a DAO object. Read-only **Boolean**. 
  
## Syntax

 *expression*  . **Updatable**
  
 *expression*  A variable that represents a **Recordset** object. 
  
## Remarks

Snapshot- and forward-only-type Recordset objects always return **False**. 
  
Many types of objects can contain fields that can't be updated. For example, you can create a dynaset-type **Recordset** object in which only some fields can be changed. These fields can be fixed or contain data that increments automatically, or the dynaset can result from a query that combines updatable and nonupdatable tables. 
  
If the object contains only read-only fields, the value of the **Updatable** property is **False**. When one or more fields are updatable, the property's value is **True**. You can edit only the updatable fields. A trappable error occurs if you try to assign a new value to a read-only field. 
  
Because an updatable object can contain read-only fields, check the **DataUpdatable** property of each field in the **Fields** collection of a **Recordset** object before you edit a record. 
  

