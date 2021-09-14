---
title: Append method (ADOX Groups)
TOCTitle: Append method (ADOX Groups)
ms:assetid: c3245a24-55b8-3f3f-1c4a-43a119d84dc8
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249954(v=office.15)
ms:contentKeyID: 48547567
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Append method (ADOX Groups)

**Applies to**: Access 2013, Office 2013

Adds a new [Group](group-object-adox.md) object to the [Groups](groups-collection-adox.md) collection.

## Syntax

*Groups*.Append*Group*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*Group* |The **Group** object to append or the name of the group to create and append.|

## Remarks

The **Groups** collection of a [Catalog](catalog-object-adox.md) represents all of the catalog's group accounts. The **Groups** collection for a [User](user-object-adox.md) represents only the group to which the user belongs.

An error will occur if the provider does not support creating groups.

> [!NOTE]
> Before appending a **Group** object to the **Groups** collection of a **User** object, a **Group** object with the same [Name](name-property-adox.md) as the one to be appended must already exist in the **Groups** collection of the **Catalog**.


