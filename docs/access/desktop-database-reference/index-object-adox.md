---
title: Index object (ADOX)
TOCTitle: Index object (ADOX)
ms:assetid: fe368ab1-e396-4684-d930-18b0ba58a925
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250304(v=office.15)
ms:contentKeyID: 48548929
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Index object (ADOX)

**Applies to**: Access 2013, Office 2013

Represents an index from a database table.

## Remarks

The following code creates a new **Index**:

`Dim obj As New Index`

With the properties and collections of an **Index** object, you can:

- Identify the index with the [Name](name-property-adox.md) property.

- Access the database columns of the index with the [Columns](columns-collection-adox.md) collection.

- Specify whether the index keys must be unique with the [Unique](unique-property-adox.md) property.

- Specify whether the index is the primary key for a table with the [PrimaryKey](primarykey-property-adox.md) property.

- Specify whether records that have null values in their index fields have index entries with the [IndexNulls](indexnulls-property-adox.md) property.

- Specify whether the index is clustered with the [Clustered](clustered-property-adox.md) property.

- Access provider-specific index properties with the [Properties](properties-collection-ado.md) collection.


> [!NOTE]
> An error will occur when appending a [Column](column-object-adox.md) to the **Columns** collection of an **Index** if the **Column** does not exist in a [Table](table-object-adox.md) object already appended to the [Tables](tables-collection-adox.md) collection.

Your data provider may not support all properties of **Index** objects. An error will occur if you have set a value for a property that is not supported by the provider. For new **Index** objects, the error will occur when the object is appended to the collection. For existing objects, the error will occur when setting the property.

When creating **Index** objects, the existence of an appropriate default value for an optional property does not guarantee that your provider supports the property. For more information about which properties your provider supports, see your provider documentation.

