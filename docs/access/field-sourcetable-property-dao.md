---
title: "Field.SourceTable Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052900
  
localization_priority: Normal
ms.assetid: 9564ea1c-eafd-0b72-fd68-d88fcc3ea189
description: "Returns a value that indicates the name of the table that is the original source of the data for a Field object. Read-only String ."
---

# Field.SourceTable Property (DAO)

Returns a value that indicates the name of the table that is the original source of the data for a **Field** object. Read-only **String**. 
  
## Syntax

 *expression*  . **SourceTable**
  
 *expression*  A variable that represents a **Field** object. 
  
## Remarks

For a **Field** object, use of the **SourceField** and **SourceTable** properties depends on the object that contains the **Fields** collection that the **Field** object is appended to, as shown in the following table. 
  
|**Object appended to**|**Usage**|
|:-----|:-----|
|**Index** <br/> |Not supported  <br/> |
|**QueryDef** <br/> |Read-only  <br/> |
|**Recordset** <br/> |Read-only  <br/> |
|**Relation** <br/> |Not supported  <br/> |
|**TableDef** <br/> |Read-only  <br/> |
   
These properties indicate the original field and table names associated with a **Field** object. For example, you could use these properties to determine the original source of the data in a query field whose name is unrelated to the name of the field in the underlying table. 
  
> [!NOTE]
> The **SourceTable** property will not return a meaningful table name if used on a **Field** object in the **Fields** collection of a table-type **Recordset** object. 
  

