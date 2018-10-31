---
title: OpenSchema Method (ADO)
TOCTitle: OpenSchema Method (ADO)
ms:assetid: 57771163-a14e-207a-2942-849acb79a9a1
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249294(v=office.15)
ms:contentKeyID: 48544970
ms.date: 09/18/2015
mtps_version: v=office.15
---

# OpenSchema Method (ADO)


**Applies to**: Access 2013 | Office 2013


Obtains database schema information from the provider .

## Syntax

**Set***recordset* = *connection*.OpenSchema (*QueryType*, *Criteria*, *SchemaID*)

## Return values

Returns a [Recordset](recordset-object-ado.md) object that contains schema information. The **Recordset** will be opened as a read-only, static cursor . The *QueryType* determines what columns appear in the **Recordset**.

## Parameters

  - *QueryType*

  - Any [SchemaEnum](schemaenum.md) value that represents the type of schema query to run.

  - *Criteria*

  - Optional. An array of query constraints for each *QueryType* option, as listed in **SchemaEnum**.

  - *SchemaID*

  - The GUID for a provider-schema query not defined by the OLE DB specification. This parameter is required if *QueryType* is set to **adSchemaProviderSpecific**; otherwise, it is not used.

## Remarks

The **OpenSchema** method returns self-descriptive information about the data source, such as what tables are in the data source, the columns in the tables, and the data types supported.

The *QueryType* argument is a GUID that indicates the columns (schemas) returned. The OLE DB specification has a full list of schemas.

The *Criteria* argument limits the results of a schema query. *Criteria* specifies an array of values that must occur in a corresponding subset of columns, called *constraint columns*, in the resulting **Recordset**.

The constant **adSchemaProviderSpecific** is used for the *QueryType* argument if the provider defines its own nonstandard schema queries outside those listed above. When this constant is used, the *SchemaID* argument is required to pass the GUID of the schema query to execute. If *QueryType* is set to **adSchemaProviderSpecific** but *SchemaID* is not provided, an error will result.

Providers are not required to support all of the OLE DB standard schema queries. Specifically, only **adSchemaTables**, **adSchemaColumns**, and **adSchemaProviderTypes** are required by the OLE DB specification. However, the provider is not required to support the *Criteria* constraints listed above for those schema queries.

**Remote Data Service Usage**The **OpenSchema** method is not available on a client-side [Connection](connection-object-ado.md) object.


> [!NOTE]
> <P>In Visual Basic, columns that have a four-byte unsigned integer (DBTYPE UI4) in the <STRONG>Recordset</STRONG> returned from the <STRONG>OpenSchema</STRONG> method on the <STRONG>Connection</STRONG> object cannot be compared to other variables. For more information about OLE DB data types, see Chapter 13 and Appendix A of the <EM>Microsoft OLE DB Programmer's Reference</EM>.</P>


