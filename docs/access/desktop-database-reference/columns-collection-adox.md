---
title: Columns Collection (ADOX)
TOCTitle: Columns Collection (ADOX)
ms:assetid: 231645db-70da-9ad1-fb27-02145ce32e66
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249008(v=office.15)
ms:contentKeyID: 48543723
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Columns Collection (ADOX)


**Applies to**: Access 2013 | Office 2013

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
> <P>An error will occur when appending a <STRONG>Column</STRONG> to the <STRONG>Columns</STRONG> collection of an <A href="index-object-adox.md">Index</A> if the <STRONG>Column</STRONG> does not exist in a <A href="table-object-adox.md">Table</A> that is already appended to the <A href="tables-collection-adox.md">Tables</A> collection.</P>


