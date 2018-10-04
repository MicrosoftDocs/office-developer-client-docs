---
title: ADO/WFC Programming
TOCTitle: ADO/WFC Programming
ms:assetid: fc438cc2-00b9-9590-6e0d-a865001ccf2f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250293(v=office.15)
ms:contentKeyID: 48548887
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ADO/WFC Programming


_**Applies to:** Access 2013 | Office 2013_

For Microsoft Visual J++ 6.0, ADO has been extended to work with Windows Foundation Classes (WFC) in the following ways. First, a set of Java classes has been implemented that extends the ADO interfaces and creates notifications interesting to the Java programmer; the Java classes also expose functions that return Java types to the user. To improve performance, the Java class directly accesses the native data types in the OLE DB rowset object, and returns them to the Java programmer as Java types without first converting them to and from a variant. ADO has also been extended to work with event notifications in the WFC framework.

ADO for Windows Foundation Classes (ADO/WFC) supports all the standard ADO methods, properties, objects, and events. However, operations that require a variant as a parameter and show excellent performance in a language such as Microsoft Visual Basic, display lesser performance in a language such as Visual J++. For that reason, ADO/WFC also provides accessor functions on the [Field](field-object-ado.md) object that take native Java data types instead of the variant data type.

For more detailed information within the ADO documentation about ADO/WFC packages, see [the ADO/WFC Syntax Index](https://msdn.microsoft.com/en-us/library/jj250066\(v=office.15\)).

## Referencing the Library

To import the ADO/WFC data classes into your project, include the following line in your code:

``` 
 
import com.ms.wfc.data.*; 
```

