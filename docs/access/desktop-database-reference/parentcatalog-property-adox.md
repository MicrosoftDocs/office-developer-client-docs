---
title: ParentCatalog property (ADOX)
TOCTitle: ParentCatalog property (ADOX)
ms:assetid: 7eef4ef5-1fa4-73ea-a710-fc8767c9ea21
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249535(v=office.15)
ms:contentKeyID: 48545891
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# ParentCatalog property (ADOX)


**Applies to**: Access 2013, Office 2013

Specifies the parent catalog of a table or column to provide access to provider-specific properties.

## Settings and return values

Sets and returns a [Catalog](catalog-object-adox.md) object. Setting **ParentCatalog** to an open **Catalog** allows access to provider-specific properties prior to appending a table or column to a **Catalog** collection.

## Remarks

Some data providers allow provider-specific property values to be written only at creation (when a table or column is appended to its **Catalog** collection). To access these properties before appending these objects to a **Catalog**, specify the **Catalog** in the **ParentCatalog** property first.

An error occurs when the table or column is appended to a different **Catalog** than the **ParentCatalog**.

