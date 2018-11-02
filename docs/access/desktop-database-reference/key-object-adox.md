---
title: Key Object (ADOX - Access desktop database reference)
TOCTitle: Key object (ADOX)
ms:assetid: 727198ec-57d2-7766-790c-370beb931de6
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249461(v=office.15)
ms:contentKeyID: 48545608
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Key object (ADOX)


**Applies to**: Access 2013, Office 2013

Represents a primary, foreign, or unique key field from a database table.

## Remarks

The following code creates a new **Key**:

`Dim obj As New Key`

With the properties and collections of a **Key** object, you can:

- Identify the key with the [Name](name-property-adox.md) property.

- Determine whether the key is primary, foreign, or unique with the [Type](https://msdn.microsoft.com/library/jj248879\(v=office.15\)) property.

- Access the database columns of the key with the [Columns](columns-collection-adox.md) collection.

- Specify the name of the related table with the [RelatedTable](relatedtable-property-adox.md) property.

- Determine the action performed on deletion or update of a primary key with the [DeleteRule](deleterule-property-adox.md) and [UpdateRule](updaterule-property-adox.md) properties.

