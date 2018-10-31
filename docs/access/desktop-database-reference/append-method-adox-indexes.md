---
title: Append Method (ADOX Indexes)
TOCTitle: Append Method (ADOX Indexes)
ms:assetid: 015ebab4-5e9d-8777-ac82-4d20e957c274
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248784(v=office.15)
ms:contentKeyID: 48542933
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Append Method (ADOX Indexes)


**Applies to**: Access 2013, Office 2013



Adds a new [Index](index-object-adox.md) object to the [Indexes](indexes-collection-adox.md) collection.

## Syntax

*Indexes*.Append*Index* \[,*Columns*\]

## Parameters

  - *Index*

  - The **Index** object to append or the name of the index to create and append.

  - *Columns*

  - Optional. A **Variant** value that specifies the name(s) of the column(s) to be indexed. The *Columns* parameter corresponds to the value(s) of the [Name](name-property-adox.md) property of a [Column](column-object-adox.md) object or objects.

## Remarks

The *Columns* parameter can take either the name of a column or an array of column names.

An error will occur if the provider does not support creating indexes.

