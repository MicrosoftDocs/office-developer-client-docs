---
title: "Field.ValidationText Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 6d9ec790-a9d2-84d7-ccba-57d738491e36
description: "Sets or returns a value that specifies the text of the message that your application displays if the value of a Field object doesn't satisfy the validation rule specified by the ValidationRule property setting (Microsoft Access workspaces only). Read/write String ."
---

# Field.ValidationText Property (DAO)

Sets or returns a value that specifies the text of the message that your application displays if the value of a **Field** object doesn't satisfy the validation rule specified by the **ValidationRule** property setting (Microsoft Access workspaces only). Read/write **String**. 
  
## Syntax

 *expression*  . **ValidationText**
  
 *expression*  A variable that represents a **Field** object. 
  
## Remarks

The setting or return value is a **String** that specifies the text displayed if a user tries to enter an invalid value for a field. For an object not yet appended to a collection, this property is read/write. 
  
For a **Field** object, use of the **ValidationText** property depends on the object that contains the **[Fields](fields-collection-dao.md)** collection to which the **Field** object is appended, as the following table shows. 
  
|**Object appended to**|**Usage**|
|:-----|:-----|
|**Index** <br/> |Not supported  <br/> |
|**QueryDef** <br/> |Read-only  <br/> |
|**Recordset** <br/> |Read-only  <br/> |
|**Relation** <br/> |Not supported  <br/> |
|**TableDef** <br/> |Read/write  <br/> |
   

