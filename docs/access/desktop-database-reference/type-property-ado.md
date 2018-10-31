---
<<<<<<< HEAD
title: Type Property (ADO)
TOCTitle: Type Property (ADO)
=======
title: Type property (ADO)
TOCTitle: Type property (ADO)
>>>>>>> master
ms:assetid: 14d99172-2145-05ae-620b-459ba097f05c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248914(v=office.15)
ms:contentKeyID: 48543397
ms.date: 09/18/2015
mtps_version: v=office.15
---

<<<<<<< HEAD
# Type Property (ADO)
=======
# Type property (ADO)
>>>>>>> master


**Applies to**: Access 2013 | Office 2013

Indicates the operational type or data type of a [Parameter](parameter-object-ado.md), [Field](field-object-ado.md), or [Property](property-object-ado.md) object.

<<<<<<< HEAD
## Settings and Return Values
=======
## Settings and return values
>>>>>>> master

Sets or returns a [DataTypeEnum](datatypeenum.md) value.

## Remarks

For **Parameter** objects, the **Type** property is read/write. For new **Field** objects that have been appended to the [Fields](fields-collection-ado.md) collection of a [Record](record-object-ado.md), **Type** is read/write only after the [Value](value-property-ado.md) property for the **Field** has been specified and the data provider has successfully added the new **Field** by calling the [Update](update-method-ado.md) method of the **Fields** collection.

For all other objects, the **Type** property is read-only.

