---
title: Delete method (ADOX Collections)
TOCTitle: Delete method (ADOX Collections)
ms:assetid: bcf9b8dd-cc7a-c1f9-fd93-58694766c4d9
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249909(v=office.15)
ms:contentKeyID: 48547423
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# Delete method (ADOX Collections)

**Applies to**: Access 2013, Office 2013

Removes an object from a collection.

## Syntax

*Collection*.Delete*Name*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*Name* |A **Variant** that specifies the name or ordinal position (index) of the object to delete.|

## Remarks

An error will occur if the *Name* does not exist in the collection.

For [Tables](tables-collection-adox.md) and [Users](users-collection-adox.md) collections, an error will occur if the provider does not support deleting tables or users, respectively. For [Procedures](procedures-collection-adox.md) and [Views](views-collection-adox.md) collections, **Delete** will fail if the provider does not support persisting commands.

