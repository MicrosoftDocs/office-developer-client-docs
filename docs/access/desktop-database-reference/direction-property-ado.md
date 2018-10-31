---
<<<<<<< HEAD
title: Direction Property (ADO)
TOCTitle: Direction Property (ADO)
=======
title: Direction property (ADO)
TOCTitle: Direction property (ADO)
>>>>>>> master
ms:assetid: 51a94abb-7ce9-9adb-2b76-5391eb9f6863
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249262(v=office.15)
ms:contentKeyID: 48544823
ms.date: 09/18/2015
mtps_version: v=office.15
---

<<<<<<< HEAD
# Direction Property (ADO)
=======
# Direction property (ADO)
>>>>>>> master


**Applies to**: Access 2013 | Office 2013

Indicates whether the [Parameter](parameter-object-ado.md) represents an input parameter, an output parameter, an input and an output parameter, or if the parameter is the return value from a stored procedure.

<<<<<<< HEAD
## Settings and Return Values
=======
## Settings and return values
>>>>>>> master

Sets or returns a [ParameterDirectionEnum](parameterdirectionenum.md) value.

## Remarks

Use the **Direction** property to specify how a parameter is passed to or from a procedure. The **Direction** property is read/write; this allows you to work with providers that don't return this information or to set this information when you don't want ADO to make an extra call to the provider to retrieve parameter information.

Not all providers can determine the direction of parameters in their stored procedures. In these cases, you must set the **Direction** property before you execute the query.

