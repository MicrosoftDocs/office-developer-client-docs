---
title: "Field2.SourceField Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: f89146c1-d4a4-1129-636a-c22cf7921a4e
description: "Returns a value that indicates the name of the field that is the original source of the data for a Field2 object. Read-only String ."
---

# Field2.SourceField Property (DAO)

Returns a value that indicates the name of the field that is the original source of the data for a **Field2** object. Read-only **String**. 
  
## Syntax

 *expression*  . **SourceField**
  
 *expression*  A variable that represents a **Field2** object. 
  
## Remarks

For a **Field2** object, use of the **SourceField** and **SourceTable** properties depends on the object that contains the **Fields** collection that the **Field2** object is appended to, as shown in the following table. 
  
|**Object appended to**|**Usage**|
|:-----|:-----|
|**Index** <br/> |Not supported  <br/> |
|**QueryDef** <br/> |Read-only  <br/> |
|**Recordset** <br/> |Read-only  <br/> |
|**Relation** <br/> |Not supported  <br/> |
|**TableDef** <br/> |Read-only  <br/> |
   
These properties indicate the original field and table names associated with a **Field2** object. For example, you could use these properties to determine the original source of the data in a query field whose name is unrelated to the name of the field in the underlying table. 
  

