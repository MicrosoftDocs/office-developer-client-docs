---
title: Keys Collection (ADOX)
TOCTitle: Keys Collection (ADOX)
ms:assetid: 0d480c01-1b36-28b9-9135-51958f313995
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248854(v=office.15)
ms:contentKeyID: 48543215
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Keys Collection (ADOX)


**Applies to**: Access 2013 | Office 2013

Contains all [Key](key-object-adox.md) objects of a table.

## Remarks

The [Append](append-method-adox-keys.md) method for a **Keys** collection is unique for ADOX. You can:

  - Add a new key to the collection with the **Append** method.

The remaining properties and methods are standard to ADO collections. You can:

  - Access a key in the collection with the [Item](item-property-ado.md) property.

  - Return the number of keys contained in the collection with the [Count](count-property-ado.md) property.

  - Remove a key from the collection with the [Delete](delete-method-adox-collections.md) method.

  - Update the objects in the collection to reflect the current database's schema with the [Refresh](refresh-method-ado.md) method.

