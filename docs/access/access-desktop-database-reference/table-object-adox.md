---
title: Table Object (ADOX)
TOCTitle: Table Object (ADOX)
ms:assetid: 53a3e2f9-4ec0-8fed-d482-4f995921587b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249273(v=office.15)
ms:contentKeyID: 48544874
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Table Object (ADOX)


_**Applies to:** Access 2013 | Office 2013_

Represents a database table including columns, indexes, and keys.

## Remarks

The following code creates a new **Table**:

    Dim obj As New Table

With the properties and collections of a **Table** object, you can:

  - Identify the table with the [Name](name-property-adox.md) property.

  - Determine the type of table with the [Type](https://msdn.microsoft.com/en-us/library/jj250042\(v=office.15\)) property.

  - Access the database columns of the table with the [Columns](columns-collection-adox.md) collection.

  - Access the indexes of the table with the [Indexes](indexes-collection-adox.md) collection.

  - Access the keys of the table with the [Keys](keys-collection-adox.md) collection.

  - Specify the [Catalog](catalog-object-adox.md) that owns the table with the [ParentCatalog](parentcatalog-property-adox.md) property.

  - Return date information with the [DateCreated](datecreated-property-adox.md) and [DateModified](datemodified-property-adox.md) properties.

  - Access provider-specific table properties with the [Properties](properties-collection-ado.md) collection.


> [!NOTE]
> <P>Your data provider may not support all properties of <STRONG>Table</STRONG> objects. An error will occur if you have set a value for a property that the provider does not support. For new <STRONG>Table</STRONG> objects, the error will occur when the object is appended to the collection. For existing objects, the error will occur when setting the property.</P>



When creating **Table** objects, the existence of an appropriate default value for an optional property does not guarantee that your provider supports the property. For more information about which properties your provider supports, see your provider documentation.

