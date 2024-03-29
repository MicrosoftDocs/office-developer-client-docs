---
title: Columns collection (ADOX)
TOCTitle: Columns collection (ADOX)
ms:assetid: 231645db-70da-9ad1-fb27-02145ce32e66
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249008(v=office.15)
ms:contentKeyID: 48543723
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Columns collection (ADOX)


**Applies to**: Access 2013, Office 2013

Contains all [Column](column-object-adox.md) objects of a table, index, or key.

## Remarks

The [Append](append-method-adox-columns.md) method for a **Columns** collection is unique for ADOX. You can:

  - Add a new column to the collection with the **Append** method.

The remaining properties and methods are standard to ADO collections. You can:

  - Access a column in the collection with the [Item](item-property-ado.md) property.

  - Return the number of columns contained in the collection with the [Count](count-property-ado.md) property.

  - Remove a column from the collection with the [Delete](delete-method-adox-collections.md) method.

  - Update the objects in the collection to reflect the current database's schema with the [Refresh](refresh-method-ado.md) method.


> [!NOTE]
> An error will occur when appending a **Column** to the **Columns** collection of an [Index](index-object-adox.md) if the **Column** does not exist in a [Table](table-object-adox.md) that is already appended to the [Tables](tables-collection-adox.md) collection.


