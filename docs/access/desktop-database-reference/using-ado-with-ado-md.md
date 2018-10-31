---
title: Using ADO with ADO MD
TOCTitle: Using ADO with ADO MD
ms:assetid: 93d1d270-b8d0-4489-d441-11a61887291c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249655(v=office.15)
ms:contentKeyID: 48546405
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Using ADO with ADO MD


**Applies to**: Access 2013, Office 2013

ADO and ADO MD are related but separate object models. ADO provides objects for connecting to data sources, executing commands, retrieving tabular data and schema metadata in a tabular format, and viewing provider error information. ADO MD provides objects for retrieving multidimensional data and viewing multidimensional schema metadata.

When working with an MDP you may choose to use ADO, ADO MD, or both with your application. By referencing both libraries within your project, you will have full access to the functionality provided by your MDP.

It is often useful for consumers to get a flattened, tabular view of a multidimensional dataset. You can do this by using the ADO [Recordset](recordset-object-ado.md) object. Specify the source for your [Cellset](cellset-object-ado-md.md) as the ***Source*** parameter for the [Open](open-method-ado-recordset.md) method of a **Recordset**, rather than as the source for an ADO MD **Cellset**.

It may also be useful to view the schema metadata in a tabular view rather than as a hierarchy of objects. The ADO [OpenSchema](openschema-method-ado.md) method on the [Connection](connection-object-ado.md) object allows the user to open a **Recordset** containing schema information. The ***QueryType*** parameter of the **OpenSchema** method has several [SchemaEnum](schemaenum.md) values that relate specifically to MDPs. These values are:

  - **adSchemaCubes**

  - **adSchemaDimensions**

  - **adSchemaHierarchies**

  - **adSchemaLevels**

  - **adSchemaMeasures**

  - **adSchemaMembers**

To use ADO enum values with ADO MD properties or methods, your project must reference both the ADO and ADO MD libraries. For example, you can use the ADO **adState** enum values with the ADO MD [State](state-property-ado-md.md) property. For more information about establishing references to libraries, see the documentation of your development tool.

For more information about the ADO objects and methods, see the [ADO API Reference](ado-api-reference.md).

