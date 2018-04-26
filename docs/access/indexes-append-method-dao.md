---
title: "Indexes.Append Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 60dce80f-505b-e988-3ac1-8ecaae3d3d09
description: "Adds a new Index to the Indexes collection."
---

# Indexes.Append Method (DAO)

Adds a new **Index** to the **Indexes** collection. 
  
## Syntax

 *expression*  . **Append**( ** *Object* ** ) 
  
 *expression*  A variable that represents an **Indexes** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Object_ <br/> |Required  <br/> |**Object** <br/> |An object variable that represents the item being appended to the collection.  <br/> |
   
## Remarks

The appended object becomes a persistent object, stored on disk, until you delete it by using the **Delete** method. 
  
The addition of a new object occurs immediately, but you should use the **Refresh** method on any other collections that may be affected by changes to the database structure. 
  
If the object you're appending isn't complete (such as when you haven't appended any **Field** objects to a **Fields** collection of an **Index** object before it's appended to an **Indexes** collection) or if the properties set in one or more subordinate objects are incorrect, using the **Append** method causes an error. For example, if you haven't specified a field type and then try to append the **Field** object to the **Fields** collection in a **TableDef** object, using the **Append** method triggers a run-time error. 
  

