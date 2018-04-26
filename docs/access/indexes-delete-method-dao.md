---
title: "Indexes.Delete Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 8d3c3221-3b2e-15ba-32ff-f2dfc592d82c
description: "Deletes the specified Index from the Indexes collection."
---

# Indexes.Delete Method (DAO)

Deletes the specified **Index** from the **Indexes** collection. 
  
## Syntax

 *expression*  . **Delete**( ** *Name* ** ) 
  
 *expression*  A variable that represents an **Indexes** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Required  <br/> |**String** <br/> |The name of the index to delete.  <br/> |
   
## Remarks

The **Delete** method is supported only when the **Index** object is new and hasn't been appended to the database. 
  

