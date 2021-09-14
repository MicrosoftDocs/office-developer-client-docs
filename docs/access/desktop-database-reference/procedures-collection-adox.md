---
title: Procedures collection (ADOX)
TOCTitle: Procedures collection (ADOX)
ms:assetid: e1ca53ad-1213-b514-e015-e18c2ab15e23
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250150(v=office.15)
ms:contentKeyID: 48548267
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Procedures collection (ADOX)


**Applies to**: Access 2013, Office 2013

Contains all [Procedure](procedure-object-adox.md) objects of a catalog.

## Remarks

The [Append](append-method-adox-procedures.md) method for a **Procedures** collection is unique for ADOX. You can:

  - Add a new procedure to the collection with the **Append** method.

The remaining properties and methods are standard to ADO collections. You can:

  - Access a procedure in the collection with the [Item](item-property-ado.md) property.

  - Return the number of procedures contained in the collection with the [Count](count-property-ado.md) property.

  - Remove a procedure from the collection with the [Delete](delete-method-adox-collections.md) method.

  - Update the objects in the collection to reflect the current database's schema with the [Refresh](refresh-method-ado.md) method.

