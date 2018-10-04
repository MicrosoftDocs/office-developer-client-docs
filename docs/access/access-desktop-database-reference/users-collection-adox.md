﻿---
title: Users Collection (ADOX)
TOCTitle: Users Collection (ADOX)
ms:assetid: bc61c862-1637-02e7-4b56-5ad984bdbcb0
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249905(v=office.15)
ms:contentKeyID: 48547413
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Users Collection (ADOX)


**Applies to**: Access 2013 | Office 2013

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
> <P>Before appending a <STRONG>User</STRONG> object to the <STRONG>Users</STRONG> collection of a <STRONG>Group</STRONG> object, a <STRONG>User</STRONG> object with the same <A href="name-property-adox.md">Name</A> as the one to be appended must already exist in the <STRONG>Users</STRONG> collection of the <STRONG>Catalog</STRONG>.</P>


