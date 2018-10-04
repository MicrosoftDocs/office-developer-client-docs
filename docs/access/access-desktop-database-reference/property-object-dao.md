﻿---
title: Property Object (DAO)
TOCTitle: Property Object
ms:assetid: a1ecb0db-bb93-a7b5-23c3-0b73f275dfe0
ms:mtpsurl: https://msdn.microsoft.com/library/Ff820932(v=office.15)
ms:contentKeyID: 48546744
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Property Object (DAO)


**Applies to**: Access 2013 | Office 2013

A **Property** object represents a built-in or user-defined characteristic of a DAO object.

## Remarks

Every DAO object except the **Connection** and **Error** objects contains a **Properties** collection which has **Property** objects corresponding to built-in properties of that DAO object. The user can also define **Property** objects and append them to the **Properties** collection of some DAO objects. These **Property** objects (which are often just called properties) uniquely characterize that instance of the object.

You can create user-defined properties for the following objects:

  - **Database**, **Index**, **QueryDef**, and **TableDef** objects

  - **Field** objects in **Fields** collections of **QueryDef** and **TableDef** objects

To add a user-defined property, use the **CreateProperty** method to create a **Property** object with a unique **Name** property setting. Set the **Type** and **Value** properties of the new **Property** object, and then append it to the **Properties** collection of the appropriate object. The object to which you are adding the user-defined property must already be appended to a collection. Referencing a user-defined **Property** object that has not yet been appended to a **Properties** collection will cause an error, as will appending a user-defined **Property** object to a **Properties** collection containing a **Property** object of the same name.

You can delete user-defined properties from the **Properties** collection, but you can't delete built-in properties.


> [!NOTE]
> <P>A user-defined <STRONG>Property</STRONG> object is associated only with the specific instance of an object. The property isn't defined for all instances of objects of the selected type.</P>



You can use the **Properties** collection of an object to enumerate the object's built-in and user-defined properties. You don't need to know beforehand exactly which properties exist or what their characteristics (**Name** and **Type** properties) are to manipulate them. However, if you try to read a write-only property, such as the **Password** property of a **Workspace** object, or try to read or write a property in an inappropriate context, such as the **Value** property setting of a **Field** object in the **Fields** collection of a **TableDef** object, an error occurs.

The **Property** object also has four built-in properties:

  - The **Name** property, a **String** that uniquely identifies the property.

  - The **Type** property, an **Integer** that specifies the property data type.

  - The **Value** property, a **Variant** that contains the property setting.

  - The **Inherited** property, a **Boolean** that indicates whether the property is inherited from another object. For example, a **Field** object in a **Fields** collection of a **Recordset** object can inherit properties from the underlying **TableDef** or **QueryDef** object.

To refer to a built-in **Property** object in a collection by its ordinal number or by its **Name** property setting, use any of the following syntax forms:

  - *object***.Properties**(0)

  - *object***.Properties**("*name*")

  - *object***.Properties**\!\[*name*\]

For a built-in property, you can also use this syntax:

  - *object*.*name*


> [!NOTE]
> <P>For a user-defined property, you must use the full <EM>object</EM><STRONG>.Properties</STRONG>("<EM>name</EM>") syntax.</P>



With the same syntax forms, you can also refer to the **Value** property of a **Property** object. The context of the reference will determine whether you are referring to the **Property** object itself or the **Value** property of the **Property** object.

