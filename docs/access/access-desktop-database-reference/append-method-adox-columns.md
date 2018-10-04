---
title: Append Method (ADOX Columns)
TOCTitle: Append Method (ADOX Columns)
ms:assetid: e256a478-abc0-f15b-fc29-1b52e354144a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250152(v=office.15)
ms:contentKeyID: 48548285
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Append Method (ADOX Columns)


**Applies to**: Access 2013 | Office 2013

Adds a new [Column](column-object-adox.md) object to the [Columns](columns-collection-adox.md) collection.

## Syntax

*Columns*. Append*Column* \[,*Type*\] \[,*DefinedSize*\]

## Parameters

  - *Column*

  - The **Column** object to append or the name of the column to create and append.

  - *Type*

  - Optional. A **Long** value that specifies the data type of the column. The *Type* parameter corresponds to the [Type](https://msdn.microsoft.com/en-us/library/jj249169\(v=office.15\)) property of a **Column** object.

  - *DefinedSize*

  - Optional. A **Long** value that specifies the size of the column. The *DefinedSize* parameter corresponds to the [DefinedSize](definedsize-property-adox.md) property of a **Column** object.


> [!NOTE]
> <P>An error will occur when appending a <STRONG>Column</STRONG> to the <STRONG>Columns</STRONG> collection of an <A href="index-object-adox.md">Index</A> if the <STRONG>Column</STRONG> does not exist in a <A href="table-object-adox.md">Table</A> that is already appended to the <A href="tables-collection-adox.md">Tables</A> collection.</P>


