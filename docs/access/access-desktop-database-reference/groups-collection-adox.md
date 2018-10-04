---
title: Groups Collection (ADOX)
TOCTitle: Groups Collection (ADOX)
ms:assetid: 9aec57df-bc5c-f9b3-5aec-e7e7efa47ba8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249702(v=office.15)
ms:contentKeyID: 48546553
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Groups Collection (ADOX)


**Applies to**: Access 2013 | Office 2013

Contains all stored [Group](group-object-adox.md) objects of a catalog or user.

## Remarks

The **Groups** collection of a [Catalog](catalog-object-adox.md) represents all of the catalog's group accounts. The **Groups** collection for a [User](user-object-adox.md) represents only the group to which the user belongs.

The [Append](append-method-adox-groups.md) method for a **Groups** collection is unique for ADOX. You can:

  - Add a new security group to the collection with the **Append** method.

The remaining properties and methods are standard to ADO collections. You can:

  - Access a group in the collection with the [Item](item-property-ado.md) property.

  - Return the number of groups contained in the collection with the [Count](count-property-ado.md) property.

  - Remove a group from the collection with the [Delete](delete-method-adox-collections.md) method.

  - Update the objects in the collection to reflect the current database's schema with the [Refresh](refresh-method-ado.md) method.


> [!NOTE]
> <P>Before appending a <STRONG>Group</STRONG> object to the <STRONG>Groups</STRONG> collection of a <STRONG>User</STRONG> object, a <STRONG>Group</STRONG> object with the same <A href="name-property-adox.md">Name</A> as the one to be appended must already exist in the <STRONG>Groups</STRONG> collection of the <STRONG>Catalog</STRONG>.</P>


