﻿---
title: Tables Collection (ADOX)
TOCTitle: Tables Collection (ADOX)
ms:assetid: 07bc0541-c528-1c25-c8c4-05736836eda3
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248821(v=office.15)
ms:contentKeyID: 48543082
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Tables Collection (ADOX)


**Applies to**: Access 2013 | Office 2013

Contains all [Table](table-object-adox.md) objects of a catalog.

## Remarks

The [Append](append-method-adox-tables.md) method for a **Tables** collection is unique for ADOX. You can:

  - Add a new table to the collection with the **Append** method.

The remaining properties and methods are standard to ADO collections. You can:

  - Access a table in the collection with the [Item](item-property-ado.md) property.

  - Return the number of tables contained in the collection with the [Count](count-property-ado.md) property.

  - Remove a table from the collection with the [Delete](delete-method-adox-collections.md) method.

  - Update the objects in the collection to reflect the current database's schema with the [Refresh](refresh-method-ado.md) method.

Some providers may return other schema objects, such as a View, in the Tables collection. Therefore, some ADOX collections may contain references to the same object. Should you delete the object from one collection, the change will not be visible in another collection that references the deleted object until the Refresh method is called on the collection. For example, with the OLE DB Provider for Microsoft Jet, Views are returned with the Tables collection. If you drop a View, you must Refresh the Tables collection before the collection will reflect the change.

