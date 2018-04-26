---
title: "Relation.CreateField Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: bc60c91e-acef-1c90-7303-12f77cce15b8
description: "Creates a new Field object (Microsoft Access workspaces only)."
---

# Relation.CreateField Method (DAO)

Creates a new **[Field](field-object-dao.md)** object (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **CreateField**( ** *Name* **, ** *Type* **, ** *Size* ** ) 
  
 *expression*  A variable that represents a **Relation** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Optional  <br/> |**Variant** <br/> |A String that uniquely names the new **Field** object. See the **[Name](connection-name-property-dao.md)** property for details on valid **Field** names.  <br/> |
| _Type_ <br/> |Optional  <br/> |**Variant** <br/> |Argument not supported for this object.  <br/> |
| _Size_ <br/> |Optional  <br/> |**Variant** <br/> |Argument not supported for this object.  <br/> |
   
### Return Value

Field
  
## Remarks

You can use the **CreateField** method to create a new field, as well as specify the name, data type, and size of the field. If you omit one or more of the optional parts when you use **CreateField**, you can use an appropriate assignment statement to set or reset the corresponding property before you append the new object to a collection. After you append the new object, you can alter some but not all of its property settings. See the individual property topics for more details. 
  
The  _type_ and  _size_ arguments apply only to **Field** objects in a **TableDef** object. These arguments are ignored when a **Field** object is associated with an **Index** or **Relation** object. 
  
If  _name_ refers to an object that is already a member of the collection, a run-time error occurs when you use the **[Append](fields-append-method-dao.md)** method. 
  
To remove a **Field** object from a **Fields** collection, use the **[Delete](fields-delete-method-dao.md)** method on the collection. You can't delete a **Field** object from a **TableDef** object's **Fields** collection after you create an index that references the field. 
  

