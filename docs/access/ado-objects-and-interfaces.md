---
title: "ADO Objects and Interfaces"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: bebf4a80-8b6e-c43c-4138-897055cc60d3
description: "The relationships between these objects are represented in the ADO Object Model."
---

# ADO Objects and Interfaces

The relationships between these objects are represented in the ADO Object Model.
  
Each object can be contained in its corresponding collection. For example, an [Error](error-object-ado.md) object can be contained in an [Errors](errors-collection-ado.md) collection. For more information, see [ADO Collections](ado-collections.md) or a specific collection topic. 
  
|||
|:-----|:-----|
|[ADORecordConstruction](adorecordconstruction-interface-ado.md) <br/> |Constructs an ADO **Record** object from an OLE DB **Row** object in a C/C++ application.  <br/> |
|[ADORecordsetConstruction](adorecordsetconstruction-interface-ado.md) <br/> |Constructs an ADO **Recordset** object from an OLE DB **Rowset** object in a C/C++ application.  <br/> |
|[Error](error-object-ado.md) <br/> |Contains details about data access errors that pertain to a single operation involving the provider.  <br/> |
|[Field](field-object-ado.md) <br/> |Represents a column of data with a common data type.  <br/> |
|[Parameter](parameter-object-ado.md) <br/> |Represents a parameter or argument associated with a **Command** object based on a parameterized query or stored procedure.  <br/> |
|[Property](property-object-ado.md) <br/> |Represents a dynamic characteristic of an ADO object that is defined by the provider.  <br/> |
|[Record](record-object-ado.md) <br/> |Represents a row of a **Recordset**, or a directory or file in a file system.  <br/> |
|[Recordset](recordset-object-ado.md) <br/> |Represents the entire set of records from a base table or the results of an executed command. At any time, the **Recordset** object refers to only a single record within the set as the current record.  <br/> |
|[Stream](stream-object-ado.md) <br/> |Represents a binary stream of data.  <br/> |
   

