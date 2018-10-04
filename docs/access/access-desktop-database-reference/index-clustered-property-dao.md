---
title: Index.Clustered Property (DAO)
TOCTitle: Clustered Property
ms:assetid: dd0876a9-b7fe-c8c8-e675-5ed758ce5bd3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff835375(v=office.15)
ms:contentKeyID: 48548149
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1052930
f1_categories:
- Office.Version=v15
---

# Index.Clustered Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

Sets or returns a value that indicates whether an **Index** object represents a clustered index for a table (Microsoft Access workspaces only). Read/write **Boolean**.

## Syntax

*expression* .Clustered

*expression* An expression that returns a **Index** object.

## Remarks

The setting or return value is a Boolean data type that is **True** if the **Index** object represents a clustered index.

Some IISAM desktop database formats use clustered indexes. A clustered index consists of one or more nonkey fields that, taken together, arrange all records in a table in a predefined order. A clustered index provides efficient access to records in a table in which the index values may not be unique.

The **Clustered** property is read/write for a new **Index** object not yet appended to a collection and read-only for an existing **Index** object in an **Indexes** collection.


> [!NOTE]
> <UL>
> <LI>
> <P>Microsoft Access database engine databases ignore the <STRONG>Clustered</STRONG> property because the Microsoft Access database engine doesn't support clustered indexes.</P>
> <LI>
> <P>For ODBC data sources the <STRONG>Clustered</STRONG> property always returns <STRONG>False</STRONG>; it does not detect whether or not the ODBC data source has a clustered index.</P></LI></UL>


