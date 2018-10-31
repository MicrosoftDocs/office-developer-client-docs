---
title: Error Object - ActiveX Data Objects (ADO)
TOCTitle: Error Object (ADO)
ms:assetid: 97e478bf-8b25-03a8-9358-abba5069cba3
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249678(v=office.15)
ms:contentKeyID: 48546477
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Error Object (ADO)


**Applies to**: Access 2013, Office 2013

Contains details about data access errors that pertain to a single operation involving the provider.

## Remarks

Any operation involving ADO objects can generate one or more provider errors. As each error occurs, one or more **Error** objects are placed in the [Errors](errors-collection-ado.md) collection of the [Connection](connection-object-ado.md) object. When another ADO operation generates an error, the **Errors** collection is cleared, and the new set of **Error** objects is placed in the **Errors** collection.

> [!NOTE]
> Each **Error** object represents a specific provider error, not an ADO error. ADO errors are exposed to the run-time exception-handling mechanism. For example, in Microsoft Visual Basic, the occurrence of an ADO-specific error will trigger an **On Error** event and appear in the **Error** object. For a complete list of ADO errors, see the [ErrorValueEnum](errorvalueenum.md) topic.

You can read an **Error** object's properties to obtain specific details about each error, including the following:

- The [Description](description-property-ado.md) property, which contains the text of the error. This is the default property.

- The [Number](number-property-ado.md) property, which contains the **Long** integer value of the error constant.

- The [Source](source-property-ado-error.md) property, which identifies the object that raised the error. This is particularly useful when you have several **Error** objects in the **Errors** collection following a request to a data source.

- The [SQLState](sqlstate-property-ado.md) and [NativeError](nativeerror-property-ado.md) properties, which provide information from SQL data sources.

When a provider error occurs, it is placed in the **Errors** collection of the **Connection** object. ADO supports the return of multiple errors by a single ADO operation to allow for error information specific to the provider. To obtain this rich error information in an error handler, use the appropriate error-trapping features of the language or environment you are working with, then use nested loops to enumerate the properties of each **Error** object in the **Errors** collection.

**Microsoft Visual Basic and VBScript Users**If there is no valid **Connection** object, you will need to retrieve error information from the **Error** object.

Just as providers do, ADO clears the **OLE Error Info** object before making a call that could potentially generate a new provider error. However, the **Errors** collection on the **Connection** object is cleared and populated only when the provider generates a new error, or when the [Clear](clear-method-ado.md) method is called.

Some properties and methods return warnings that appear as **Error** objects in the **Errors** collection but do not halt a program's execution. Before you call the [Resync](resync-method-ado.md), [UpdateBatch](updatebatch-method-ado.md), or [CancelBatch](cancelbatch-method-ado.md) methods on a [Recordset](recordset-object-ado.md) object; the [Open](open-method-ado-connection.md) method on a **Connection** object; or set the [Filter](filter-property-ado.md) property on a **Recordset** object, call the **Clear** method on the **Errors** collection. That way, you can read the [Count](count-property-ado.md) property of the **Errors** collection to test for returned warnings.

