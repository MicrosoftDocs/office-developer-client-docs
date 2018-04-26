---
title: "Index.Required Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052963
  
localization_priority: Normal
ms.assetid: ec8fafc4-8155-c48e-b3c8-2d9be425175a
description: "Sets or returns a value that indicates whether a Field object requires a non-Null value."
---

# Index.Required Property (DAO)

Sets or returns a value that indicates whether a **[Field](field-object-dao.md)** object requires a non-Null value. 
  
## Syntax

 *expression*  . **Required**
  
 *expression*  A variable that represents an **Index** object. 
  
## Remarks

> [!NOTE]
> When you can set this property for either an **Index** object or a **Field** object, set it for the **Field** object. The validity of the property setting for a **Field** object is checked before that of an **Index** object. 
  
The availability of the **Required** property depends on the object that contains the [Fields](fields-collection-dao.md) collection, as shown in the following table. 
  
|**If the Fields collection belongs to a**|**Then Required is**|
|:-----|:-----|
|**Index** object  <br/> |Not supported  <br/> |
|**QueryDef** object  <br/> |Read-only  <br/> |
|**Recordset** object  <br/> |Read-only  <br/> |
|**Relation** object  <br/> |Not supported  <br/> |
|**TableDef** object  <br/> |Read/write  <br/> |
   

