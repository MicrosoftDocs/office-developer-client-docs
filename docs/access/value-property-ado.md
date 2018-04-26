---
title: "Value Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ff21d122-98e3-2b48-d92f-e696b8079fc5

---

# Value Property (ADO)

Indicates the value assigned to a [Field](field-object-ado.md), [Parameter](parameter-object-ado.md), or [Property](property-object-ado.md) object. 
  
## Settings and Return Values

Sets or returns a **Variant** value that indicates the value of the object. Default value depends on the [Type](type-property-ado.md) property. 
  
## Remarks

Use the **Value** property to set or return data from **Field** objects, to set or return parameter values with **Parameter** objects, or to set or return property settings with **Property** objects. Whether the **Value** property is read/write or read-only depends upon numerous factors — see the respective object topics for more information. 
  
ADO allows setting and returning long binary data with the **Value** property. 
  
> [!NOTE]
> For **Parameter** objects, ADO reads the **Value** property only once from the provider. If a command contains a **Parameter** whose **Value** property is empty, and you create a [Recordset](recordset-object-ado.md) from the command, ensure that you first close the **Recordset** before retrieving the **Value** property. Otherwise, for some providers, the **Value** property may be empty, and won't contain the correct value. 
  
For new **Field** objects that have been appended to the [Fields](fields-collection-ado.md) collection of a [Record](record-object-ado.md) object, the **Value** property must be set before any other **Field** properties can be specified. First, a specific value for the **Value** property must have been assigned and [Update](update-method-ado.md) on the **Fields** collection called. Then, other properties such as [Type](type-property-ado.md) or [Attributes](attributes-property-ado.md) can be accessed. 
  

