---
title: Append method (ADOX Tables)
TOCTitle: Append method (ADOX Tables)
ms:assetid: 9e9fd57c-a856-6179-013f-9f378c3b7df0
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249726(v=office.15)
ms:contentKeyID: 48546664
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Append method (ADOX Tables)

**Applies to**: Access 2013, Office 2013

Adds a new [Table](table-object-adox.md) object to the [Tables](tables-collection-adox.md) collection.

## Syntax

*Tables*.Append*Table*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*Table* | A **Variant** value that contains a reference to the **Table** to append or the name of the table to create and append.|

## Remarks

An error will occur if the provider does not support creating tables.

