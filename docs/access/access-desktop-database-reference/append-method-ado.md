﻿---
title: Append Method (ADO)
TOCTitle: Append Method (ADO)
ms:assetid: cca133af-2b95-877d-0488-0d99631623f2
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250014(v=office.15)
ms:contentKeyID: 48547742
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Append Method (ADO)


**Applies to**: Access 2013 | Office 2013



Appends an object to a collection. If the collection is [Fields](fields-collection-ado.md), a new [Field](field-object-ado.md) object may be created before it is appended to the collection.

## Syntax

*collection*.Append *object*

*fields*.Append *Name*, *Type*, *DefinedSize*, *Attrib*, *FieldValue*

## Parameters

  - *collection*

  - A collection object.

  - *fields*

  - A **Fields** collection.

  - *object*

  - An object variable that represents the object to be appended.

  - *Name*

  - A **String** value that contains the name of the new **Field** object, and must not be the same name as any other object in *fields*.

  - *Type*

  - A [DataTypeEnum](datatypeenum.md) value, whose default value is **adEmpty**, that specifies the data type of the new field. The following data types are not supported by ADO, and should not be used when appending new fields to a **Recordset**: **adIDispatch**, **adIUnknown**, **adVariant**.

  - *DefinedSize*

  - Optional. A **Long** value that represents the defined size, in characters or bytes, of the new field. The default value for this parameter is derived from *Type*. Fields with a DefinedSize greater than 255 bytes, and treated as variable length columns. (The default *DefinedSize* is unspecified.)

  - *Attrib*

  - Optional. A [FieldAttributeEnum](fieldattributeenum.md) value, whose default value is **adFldDefault**, that specifies attributes for the new field. If this value is not specified, the field will contain attributes derived from *Type*.

  - *FieldValue*

  - Optional. A **Variant** that represents the value for the new field. If not specified, then the field is appended with a null value.

## Remarks

**Parameters Collection**

You must set the [Type](type-property-ado.md) property of a [Parameter](parameter-object-ado.md) object before appending it to the **Parameters** collection. If you select a variable-length data type, you must also set the [Size](size-property-ado.md) property to a value greater than zero.

Describing parameters yourself minimizes calls to the provider and consequently improves performance when using stored procedures or parameterized queries. However, you must know the properties of the parameters associated with the stored procedure or parameterized query that you want to call.

Use the [CreateParameter](createparameter-method-ado.md) method to create **Parameter** objects with the appropriate property settings and use the **Append** method to add them to the [Parameters](parameters-collection-ado.md) collection. This lets you set and return parameter values without having to call the provider for the parameter information. If you are writing to a provider that does not supply parameter information, you must use this method to manually populate the **Parameters** collection in order to use parameters at all.

**Fields Collection**

The *FieldValue* parameter is only valid when adding a **Field** object to a [Record](record-object-ado.md) object, not to a **Recordset** object. With a **Record** object, you may append fields and provide values at the same time. With a **Recordset** object, you must create fields while the **Recordset** is closed, then open the **Recordset** and assign values to the fields.


> [!NOTE]
> <P>For new <STRONG>Field</STRONG> objects that have been appended to the <STRONG>Fields</STRONG> collection of a <STRONG>Record</STRONG> object, the <A href="value-property-ado.md">Value</A> property must be set before any other <STRONG>Field</STRONG> properties can be specified. First, a specific value for the <STRONG>Value</STRONG> property must have been assigned and <A href="update-method-ado.md">Update</A> on the <STRONG>Fields</STRONG> collection called. Then, other properties such as <A href="type-property-ado.md">Type</A> or <A href="attributes-property-ado.md">Attributes</A> can be accessed.</P>



**Field** objects of the following data types (**DataTypeEnum**) cannot be appended to the **Fields** collection and will cause an error to occur: **adArray**, **adChapter**, **adEmpty**, **adPropVariant**, and **adUserDefined**. Also, the following data types are not supported by ADO: **adIDispatch**, **adIUnknown**, and **adIVariant**. For these types, no error will occur when appended, but usage can produce unpredictable results including memory leaks.

**Recordset**

If you do not set the [CursorLocation](cursorlocation-property-ado.md) property before calling the **Append** method, **CursorLocation** will be set to **adUseClient** (a [CursorLocationEnum](cursorlocationenum.md) value) automatically when the [Recordset](recordset-object-ado.md) object's [Open](open-method-ado-recordset.md) method is called.

A run-time error will occur if the **Append** method is called on the **Fields** collection of an open **Recordset**, or on a **Recordset** where the [ActiveConnection](activeconnection-property-ado.md) property has been set. You can only append fields to a **Recordset** that is not open and has not yet been connected to a data source. This is typically the case when a **Recordset** object is fabricated with the [CreateRecordset](createrecordset-method-rds.md) method or assigned to an object variable.

**Record**

A run-time error will not occur if the **Append** method is called on the **Fields** collection of an open **Record**. The new field will be added to the **Record** object's **Fields** collection. If the **Record** was derived from a **Recordset**, then the new field will not appear in the **Recordset** object's **Fields** collection.

A non-existent field can be created and appended to the **Fields** collection by assigning a value to the field object as if it already existed in the collection. The assignment will trigger the automatic creation and appending of the **Field** object, then the assignment will be completed.

After appending a **Field** to a **Record** object's **Fields** collection, call the **Update** method of the **Fields** collection to save the change.

