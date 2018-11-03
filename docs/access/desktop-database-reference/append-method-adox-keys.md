---
title: Append method (ADOX Keys)
TOCTitle: Append method (ADOX Keys)
ms:assetid: 14d6e8d7-5c9e-a422-47d6-ebfd9dd7a120
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248913(v=office.15)
ms:contentKeyID: 48543396
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Append method (ADOX Keys)

**Applies to**: Access 2013, Office 2013

Adds a new [Key](key-object-adox.md) object to the [Keys](keys-collection-adox.md) collection.

## Syntax

*Keys*.Append*Key* \[,*KeyType*\] \[,*Column*\] \[,*RelatedTable*\] \[,*RelatedColumn*\]

## Parameters

|Parameter|Description|
|:--------|:----------|
|*Key* |The **Key** object to append or the name of the key to create and append.|
|*KeyType* |Optional. A **Long** value that specifies the type of key. The *Key* parameter corresponds to the [Type](https://docs.microsoft.com/office/vba/access/concepts/miscellaneous/type-property-keyadox) property of a **Key** object.|
|*Column* |Optional. A **String** value that specifies the name of the column to be indexed. The *Columns* parameter corresponds to the value of the [Name](name-property-adox.md) property of a [Column](column-object-adox.md) object.|
|*RelatedTable* |Optional. A **String** value that specifies the name of the related table. The *RelatedTable* parameter corresponds to the value of the **Name** property of a [Table](table-object-adox.md) object.|
|*RelatedColumn* |Optional. A **String** value that specifies the name of the related column for a foreign key. The RelatedColumn parameter corresponds to the value of the **Name** property of a **Column** object.|

## Remarks

The *Columns* parameter can take either the name of a column or an array of column names.

