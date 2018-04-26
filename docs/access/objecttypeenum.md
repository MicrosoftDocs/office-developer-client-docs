---
title: "ObjectTypeEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: b0ee2113-dea9-912d-3442-e54885397310

---

# ObjectTypeEnum

Specifies the type of database object for which to set permissions or ownership.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adPermObjColumn** <br/> |2  <br/> |The object is a column.  <br/> |
|**adPermObjDatabase** <br/> |3  <br/> |The object is a database.  <br/> |
|**adPermObjProcedure** <br/> |4  <br/> |The object is a procedure.  <br/> |
|**adPermObjProviderSpecific** <br/> |-1  <br/> |The object is a type defined by the provider. An error will occur if the  *ObjectType*  parameter is **adPermObjProviderSpecific** and an  *ObjectTypeId*  is not supplied.  <br/> |
|**adPermObjTable** <br/> |1  <br/> |The object is a table.  <br/> |
|**adPermObjView** <br/> |5  <br/> |The object is a view.  <br/> |
   

