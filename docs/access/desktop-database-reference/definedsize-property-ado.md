---
<<<<<<< HEAD
title: DefinedSize Property (ADO)
TOCTitle: DefinedSize Property (ADO)
=======
title: DefinedSize property (ADO)
TOCTitle: DefinedSize property (ADO)
>>>>>>> master
ms:assetid: 8d6db4c9-fbdc-9fcd-63f0-bd677c5ebcf6
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249619(v=office.15)
ms:contentKeyID: 48546257
ms.date: 09/18/2015
mtps_version: v=office.15
---

<<<<<<< HEAD
# DefinedSize Property (ADO)
=======
# DefinedSize property (ADO)
>>>>>>> master


**Applies to**: Access 2013 | Office 2013

Indicates the data capacity of a [Field](field-object-ado.md) object.

<<<<<<< HEAD
## Return Value
=======
## Return value
>>>>>>> master

Returns a **Long** value that reflects the defined size of a field as a number of bytes.

## Remarks

Use the **DefinedSize** property to determine the data capacity of a **Field** object.

The **DefinedSize** and [ActualSize](actualsize-property-ado.md) properties are different. For example, consider a **Field** object with a declared type of **adVarChar** and a **DefinedSize** property value of 50, containing a single character. The **ActualSize** property value it returns is the length in bytes of the single character.

