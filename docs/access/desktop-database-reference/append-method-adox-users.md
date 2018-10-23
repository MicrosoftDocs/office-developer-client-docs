---
title: Append Method (ADOX Users)
TOCTitle: Append Method (ADOX Users)
ms:assetid: b7a1128b-c6e7-2071-c914-913b6bd245ae
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249884(v=office.15)
ms:contentKeyID: 48547302
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Append Method (ADOX Users)


**Applies to**: Access 2013 | Office 2013


Adds a new [User](user-object-adox.md) object to the [Users](users-collection-adox.md) collection.

## Syntax

*Users*.Append*User*\[,*Password*\]

## Parameters

  - *User*

  - A **Variant** value that contains the **User** object to append or the name of the user to create and append.

  - *Password*

  - Optional. A **String** value that contains the password for the user. The *Password* parameter corresponds to the value specified by the [ChangePassword](changepassword-method-adox.md) method of a **User** object.

## Remarks

The **Users** collection of a [Catalog](catalog-object-adox.md) represents all the catalog's users. The **Users** collection for a [Group](group-object-adox.md) represents only the users that have a membership in the specific group.

An error will occur if the provider does not support creating users.


> [!NOTE]
> Before appending a **User** object to the **Users** collection of a **Group** object, a **User** object with the same [Name](name-property-adox.md) as the one to be appended must already exist in the **Users** collection of the **Catalog**.


