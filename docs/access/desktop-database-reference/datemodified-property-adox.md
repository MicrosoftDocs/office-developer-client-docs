---
title: DateModified property (ADOX)
TOCTitle: DateModified property (ADOX)
ms:assetid: aebe8818-82e7-84a4-24d7-d97afa32e193
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249827(v=office.15)
ms:contentKeyID: 48547078
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# DateModified property (ADOX)


**Applies to**: Access 2013, Office 2013

Indicates the date the object was last modified.

## Return values

Returns a **Variant** value specifying the date modified. The value is null if **DateModified** is not supported by the provider.

## Remarks

The **DateModified** property is null for newly appended objects. After appending a new [View](view-object-adox.md) or [Procedure](procedure-object-adox.md), you must call the [Refresh](refresh-method-ado.md) method of the [Views](views-collection-adox.md) or [Procedures](procedures-collection-adox.md) collection to obtain values for the **DateModified** property.

