---
title: "Type Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 14d99172-2145-05ae-620b-459ba097f05c

---

# Type Property (ADO)

Indicates the operational type or data type of a [Parameter](parameter-object-ado.md), [Field](field-object-ado.md), or [Property](property-object-ado.md) object. 
  
## Settings and Return Values

Sets or returns a [DataTypeEnum](datatypeenum.md) value. 
  
## Remarks

For **Parameter** objects, the **Type** property is read/write. For new **Field** objects that have been appended to the [Fields](fields-collection-ado.md) collection of a [Record](record-object-ado.md), **Type** is read/write only after the [Value](value-property-ado.md) property for the **Field** has been specified and the data provider has successfully added the new **Field** by calling the [Update](update-method-ado.md) method of the **Fields** collection. 
  
For all other objects, the **Type** property is read-only. 
  

