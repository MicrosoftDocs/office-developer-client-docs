---
title: "ADO Dynamic Properties"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: a908bc52-2cb0-89c7-a997-2cde93477e4d
description: "Dynamic properties can be added to the Properties collections of the Connection, Command, or Recordset objects. The source for these properties is either a data provider, such as the OLE DB Provider for SQL Server, or a service provider, such as the Microsoft Cursor Service for OLE DB. Refer to the appropriate data provider or service provider documentation for more information about a specific dynamic property."
---

# ADO Dynamic Properties

Dynamic properties can be added to the [Properties](properties-collection-ado.md) collections of the [Connection](connection-object-ado.md), [Command](command-object-ado.md), or [Recordset](recordset-object-ado.md) objects. The source for these properties is either a data provider, such as the [OLE DB Provider for SQL Server](microsoft-ole-db-provider-for-sql-server.md), or a service provider, such as the [Microsoft Cursor Service for OLE DB](microsoft-cursor-service-for-ole-db-ado-service-component.md). Refer to the appropriate data provider or service provider documentation for more information about a specific dynamic property.
  
The [ADO Dynamic Property Index](ado-dynamic-property-index.md) provides a cross-reference between the ADO and OLE DB names for each standard OLE DB provider dynamic property. 
  
The following dynamic properties are of special interest, and are also documented in the sources mentioned above. Special functionality with ADO is documented in the ADO help topics listed below.
  
|||
|:-----|:-----|
|[Optimize](optimize-property-dynamic-ado.md) <br/> |Specifies whether an index should be created on this field.  <br/> |
|[Prompt](prompt-property-dynamic-ado.md) <br/> |Specifies whether the OLE DB provider should prompt the user for initialization information.  <br/> |
|[Reshape Name](reshape-name-property-dynamic-ado.md) <br/> |Specifies a name for the **Recordset** object.  <br/> |
|[Resync Command](resync-command-property-dynamic-ado.md) <br/> |Specifies a user-supplied command string that the **Resync** method issues to refresh the data in the table named in the **Unique Table** dynamic property.  <br/> |
|[Unique Table, Unique Schema, Unique Catalog](unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) <br/> |**Unique Table** — specifies the name of the base table upon which updates, insertions, and deletions are allowed. **Unique Schema** — specifies the schema, or name of the owner of the table. **Unique Catalog** — specifies the catalog, or name of the database containing the table.  <br/> |
|[Update Resync](update-resync-property-dynamic-ado.md) <br/> |Specifies whether the **UpdateBatch** method is followed by an implicit **Resync** method operation, and if so, the scope of that operation.  <br/> |
   

