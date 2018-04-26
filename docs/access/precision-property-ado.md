---
title: "Precision Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: c9d54d78-d5a5-caf8-d635-259d1fcc0595

---

# Precision Property (ADO)

Indicates the degree of precision for numeric values in a [Parameter](parameter-object-ado.md) object or for numeric [Field](field-object-ado.md) objects. 
  
## Settings and Return Values

Sets or returns a **Byte** value that indicates the maximum number of digits used to represent values. 
  
## Remarks

Use the **Precision** property to determine the maximum number of digits used to represent values for a numeric **Parameter** or **Field** object. 
  
The value is read/write on a **Parameter** object. 
  
For a **Field** object, **Precision** is normally read-only. However, for new **Field** objects that have been appended to the [Fields](fields-collection-ado.md) collection of a [Record](record-object-ado.md), **Precision** is read/write only after the [Value](value-property-ado.md) property for the **Field** has been specified and the data provider has successfully added the new **Field** by calling the [Update](update-method-ado.md) method of the **Fields** collection. 
  

