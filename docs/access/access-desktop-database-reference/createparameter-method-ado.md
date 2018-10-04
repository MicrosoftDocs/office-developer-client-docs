---
title: CreateParameter Method (ADO)
TOCTitle: CreateParameter Method (ADO)
ms:assetid: cf080a0b-75d2-dcdf-2715-10af147358e9
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250026(v=office.15)
ms:contentKeyID: 48547799
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- ado210.chm1231042
f1_categories:
- Office.Version=v15
---

# CreateParameter Method (ADO)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Return Value  
Parameters  
Remarks  

Creates a new [Parameter](parameter-object-ado.md) object with the specified properties.

## Syntax

**Set** *parameter* = *command*.CreateParameter (*Name*, *Type*, *Direction*, *Size*, *Value*)

## Return Value

Returns a **Parameter** object.

## Parameters

  - *Name*

  - Optional. A **String** value that contains the name of the **Parameter** object.

  - *Type*

  - Optional. A [DataTypeEnum](datatypeenum.md) value that specifies the data type of the **Parameter** object.

  - *Direction*

  - Optional. A [ParameterDirectionEnum](parameterdirectionenum.md) value that specifies the type of **Parameter** object.

  - *Size*

  - Optional. A **Long** value that specifies the maximum length for the parameter value in characters or bytes.

  - *Value*

  - Optional. A **Variant** that specifies the value for the **Parameter** object.

## Remarks

Use the **CreateParameter** method to create a new **Parameter** object with a specified name, type, direction, size, and value. Any values you pass in the arguments are written to the corresponding **Parameter** properties.

This method does not automatically append the **Parameter** object to the **Parameters** collection of a [Command](command-object-ado.md) object. This lets you set additional properties whose values ADO will validate when you append the **Parameter** object to the collection.

If you specify a variable-length data type in the *Type* argument, you must either pass a *Size* argument or set the [Size](size-property-ado.md) property of the **Parameter** object before appending it to the **Parameters** collection; otherwise, an error occurs.

If you specify a numeric data type (**adNumeric** or **adDecimal**) in the *Type* argument, then you must also set the [NumericScale](numericscale-property-ado.md) and [Precision](precision-property-ado.md) properties.

