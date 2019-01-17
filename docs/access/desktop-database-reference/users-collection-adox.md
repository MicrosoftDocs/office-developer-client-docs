---
title: Users collection (ADOX)
TOCTitle: Users collection (ADOX)
ms:assetid: bc61c862-1637-02e7-4b56-5ad984bdbcb0
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249905(v=office.15)
ms:contentKeyID: 48547413
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# Users collection (ADOX)

**Applies to**: Access 2013, Office 2013

Contains all stored [User](user-object-adox.md) objects of a catalog or group.

## Remarks

The **Users** collection of a [Catalog](catalog-object-adox.md) represents all the catalog's users. The **Users** collection for a [Group](group-object-adox.md) represents only the users that have a membership in the specific group.

The [Append](append-method-adox-users.md) method for a **Users** collection is unique for ADOX. You can:

- Add a new user to the collection with the **Append** method.

The remaining properties and methods are standard to ADO collections. You can:

- Access a user in the collection with the [Item](item-property-ado.md) property.

- Return the number of users contained in the collection with the [Count](count-property-ado.md) property.

- Remove a user from the collection with the [Delete](delete-method-adox-collections.md) method.

- Update the objects in the collection to reflect the current database's schema with the [Refresh](refresh-method-ado.md) method.

> [!NOTE]
> Before appending a **User** object to the **Users** collection of a **Group** object, a **User** object with the same [Name](name-property-adox.md) as the one to be appended must already exist in the **Users** collection of the **Catalog**.

