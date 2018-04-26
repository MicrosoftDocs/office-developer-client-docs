---
title: "TableDefs.Delete Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 130bb50d-17c3-b2ab-9360-0d91d0cee131
description: "Deletes the specified TableDef object from the TableDefs collection."
---

# TableDefs.Delete Method (DAO)

Deletes the specified **TableDef** object from the **TableDefs** collection. 
  
## Syntax

 *expression*  . **Delete**( ** *Name* ** ) 
  
 *expression*  A variable that represents a **TableDefs** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Required  <br/> |**String** <br/> |The name of the TableDef to delete.  <br/> |
   
## Remarks

The Delete method is supported only when the **TableDef** object is new and hasn't been appended to the database, or when the **Updatable** property of the **TableDef** is set to **True**. 
  

