---
title: Property Object (ADO)
TOCTitle: Property Object (ADO)
ms:assetid: eec318fd-f5ed-d9ef-9830-848439a8914d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250210(v=office.15)
ms:contentKeyID: 48548567
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Property Object (ADO)


**Applies to**: Access 2013 | Office 2013

Represents a dynamic characteristic of an ADO object that is defined by the provider.

## Remarks

ADO objects have two types of properties: built-in and dynamic.

Built-in properties are those properties implemented in ADO and immediately available to any new object, using the syntax. They do not appear as **Property** objects in an object's [Properties](properties-collection-ado.md) collection, so although you can change their values, you cannot modify their characteristics.

Dynamic properties are defined by the underlying data provider, and appear in the **Properties** collection for the appropriate ADO object. For example, a property specific to the provider may indicate if a [Recordset](recordset-object-ado.md) object supports transactions or updating. These additional properties will appear as **Property** objects in that **Recordset** object's **Properties** collection. Dynamic properties can be referenced only through the collection, using the MyObject.Properties(0) or or MyObject.Properties("Name") syntax.

You cannot delete either kind of property.

A dynamic **Property** object has four built-in properties of its own:

  - The [Name](name-property-ado.md) property is a string that identifies the property.

  - The [Type](type-property-ado.md) property is an integer that specifies the property data type.

  - The [Value](value-property-ado.md) property is a variant that contains the property setting. **Value** is the default property for a **Property** object.

  - The [Attributes](attributes-property-ado.md) property is a long value that indicates characteristics of the property specific to the provider.

