---
title: View Object (ADOX - Access desktop database reference)
TOCTitle: View Object (ADOX)
ms:assetid: 3b2e9972-8a0d-eaa3-1c93-ae0665a47f02
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249149(v=office.15)
ms:contentKeyID: 48544280
ms.date: 09/18/2015
mtps_version: v=office.15
---

# View Object (ADOX)


**Applies to**: Access 2013, Office 2013

Represents a filtered set of records or a virtual table. When used in conjunction with the ADO [Command](command-object-ado.md) object, the **View** object can be used for adding, deleting, or modifying views.

## Remarks

A view is a virtual table, created from other database tables or views. The **View** object allows you to create a view without having to know or use the provider's "CREATE VIEW" syntax.

With the properties of a **View** object, you can:

  - Identify the view with the [Name](name-property-adox.md) property.

  - Specify the ADO **Command** object that can be used to add, delete, or modify views with the [Command](command-property-adox.md) property.

  - Return date information with the [DateCreated](datecreated-property-adox.md) and [DateModified](datemodified-property-adox.md) properties.

