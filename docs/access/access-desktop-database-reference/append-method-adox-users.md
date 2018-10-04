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

**In this article**  
Syntax  
Parameters  
Remarks  

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
> <P>Before appending a <STRONG>User</STRONG> object to the <STRONG>Users</STRONG> collection of a <STRONG>Group</STRONG> object, a <STRONG>User</STRONG> object with the same <A href="name-property-adox.md">Name</A> as the one to be appended must already exist in the <STRONG>Users</STRONG> collection of the <STRONG>Catalog</STRONG>.</P>


