---
title: Append method (ADOX Columns)
TOCTitle: Append method (ADOX Columns)
ms:assetid: e256a478-abc0-f15b-fc29-1b52e354144a
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250152(v=office.15)
ms:contentKeyID: 48548285
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Append method (ADOX Columns)

**Applies to**: Access 2013, Office 2013

Adds a new [Column](column-object-adox.md) object to the [Columns](columns-collection-adox.md) collection.

## Syntax

*Columns*. Append*Column* \[,*Type*\] \[,*DefinedSize*\]

## Parameters

|Parameter|Description|
|:--------|:----------|
|*Column* |The **Column** object to append or the name of the column to create and append.|
|*Type* |Optional. A **Long** value that specifies the data type of the column. The *Type* parameter corresponds to the [Type](https://docs.microsoft.com/office/vba/access/concepts/miscellaneous/type-property-columnadox) property of a **Column** object.|
|*DefinedSize* |Optional. A **Long** value that specifies the size of the column. The *DefinedSize* parameter corresponds to the [DefinedSize](definedsize-property-adox.md) property of a **Column** object.|


> [!NOTE]
> An error will occur when appending a **Column** to the **Columns** collection of an [Index](index-object-adox.md) if the **Column** does not exist in a [Table](table-object-adox.md) that is already appended to the [Tables](tables-collection-adox.md) collection.


