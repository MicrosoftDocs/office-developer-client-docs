---
title: Property.Name Property (DAO)
TOCTitle: Name Property
ms:assetid: 0dae15e0-5d2e-3bb4-8a44-98db4a8ce516
ms:mtpsurl: https://msdn.microsoft.com/library/Ff845211(v=office.15)
ms:contentKeyID: 48543225
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Property.Name Property (DAO)


**Applies to**: Access 2013 | Office 2013

Returns or sets the name of the specified object. Read/write **String** if the object has not been appended to a collection. Read-only **String** if the object has been appended to a collection.

## Syntax

*expression* .Name

*expression* A variable that represents a **Property** object.

## Remarks

The **Name** property of a built-in property is always read-only.

The maximum length for the name of a **Property** object is 64 characters.

