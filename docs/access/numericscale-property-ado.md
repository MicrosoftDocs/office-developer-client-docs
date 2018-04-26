---
title: "NumericScale Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 51b232d2-5bfd-521c-f4e9-65655ecc7c70

---

# NumericScale Property (ADO)

Indicates the scale of numeric values in a [Parameter](parameter-object-ado.md) or [Field](field-object-ado.md) object. 
  
## Settings and Return Values

Sets or returns a **Byte** value that indicates the number of decimal places to which numeric values will be resolved. 
  
## Remarks

Use the **NumericScale** property to determine how many digits to the right of the decimal point will be used to represent values for a numeric **Parameter** or **Field** object. 
  
For **Parameter** objects, the **NumericScale** property is read/write. 
  
For a **Field** object, **NumericScale** is normally read-only. However, for new **Field** objects that have been appended to the [Fields](fields-collection-ado.md) collection of a [Record](record-object-ado.md), **NumericScale** is read/write only after the [Value](value-property-ado.md) property for the **Field** has been specified and the data provider has successfully added the new **Field** by calling the [Update](update-method-ado.md) method of the **Fields** collection. 
  

