---
title: "Document.CreateProperty Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1052967
  
localization_priority: Normal
ms.assetid: 834fda60-1edf-38df-a9a5-d9d15e55e425
description: "Creates a new user-defined Property object (Microsoft Access workspaces only)."
---

# Document.CreateProperty Method (DAO)

Creates a new user-defined **[Property](property-object-dao.md)** object (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **CreateProperty**( ** *Name* **, ** *Type* **, ** *Value* **, ** *DDL* ** ) 
  
 *expression*  A variable that represents a **Document** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Optional  <br/> |**Variant** <br/> |A **String** that uniquely names the new **Property** object. See the **Name** property for details on valid **Property** names.  <br/> |
| _Type_ <br/> |Optional  <br/> |**Variant** <br/> | A constant that defines the data type of the new **Property** object. See the **[Type](field-type-property-dao.md)** property for valid data types.  <br/> |
| _Value_ <br/> |Optional  <br/> |**Variant** <br/> |A **Variant** containing the initial property value. See the **[Value](field-value-property-dao.md)** property for details.  <br/> |
| _DDL_ <br/> |Optional  <br/> |**Variant** <br/> |A **Variant** ( **Boolean** subtype) that indicates whether or not the **Property** is a DDL object. The default is **False**. If  _DDL_ is **True**, users can't change or delete this **Property** object unless they have **dbSecWriteDef** permission.  <br/> |
   
### Return Value

Property
  
## Remarks

You can create a user-defined **Property** object only in the **[Properties](properties-collection-dao.md)** collection of an object that is persistent. 
  
If you omit one or more of the optional parts when you use **CreateProperty**, you can use an appropriate assignment statement to set or reset the corresponding property before you append the new object to a collection. After you append the object, you can alter some but not all of its property settings. See the **Name**, **Type**, and **Value** property topics for more details. 
  
If  _name_ refers to an object that is already a member of the collection, a run-time error occurs when you use the **[Append](fields-append-method-dao.md)** method. 
  
To remove a user-defined **Property** object from the collection, use the **[Delete](fields-delete-method-dao.md)** method on the **Properties** collection. You can't delete built-in properties. 
  
> [!NOTE]
> If you omit the  _DDL_ argument, it defaults to  _False_ (non-DDL). Because no corresponding DDL property is exposed, you must delete and re-create a **Property** object you want to change from DDL to non-DDL. 
  

