---
title: Indexes collection (ADOX)
TOCTitle: Indexes collection (ADOX)
ms:assetid: ab04bdd1-7c4a-44cb-dfc6-add3a52f502f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249793(v=office.15)
ms:contentKeyID: 48546963
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Indexes collection (ADOX)


**Applies to**: Access 2013, Office 2013

Contains all [Index](index-object-adox.md) objects of a table.

## Remarks

The [Append](append-method-adox-indexes.md) method for an **Indexes** collection is unique for ADOX. You can:

  - Add a new index to the collection with the **Append** method.

The remaining properties and methods are standard to ADO collections. You can:

  - Access an index in the collection with the [Item](item-property-ado.md) property.

  - Return the number of indexes contained in the collection with the [Count](count-property-ado.md) property.

  - Remove an index from the collection with the [Delete](delete-method-adox-collections.md) method.

  - Update the objects in the collection to reflect the current database's schema with the [Refresh](refresh-method-ado.md) method.

