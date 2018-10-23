---
title: Name Property (ADOX)
TOCTitle: Name Property (ADOX)
ms:assetid: c92a3b2b-6e3f-1ed9-c7be-bf348a0737af
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249979(v=office.15)
ms:contentKeyID: 48547674
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Name Property (ADOX)


**Applies to**: Access 2013 | Office 2013

Indicates the name of the object.

## Settings and return values

Sets or returns a **String** value.

## Remarks

Names do not have to be unique within a collection.

The **Name** property is read/write on [Column](column-object-adox.md), [Group](group-object-adox.md), [Key](key-object-adox.md), [Index](index-object-adox.md), [Table](table-object-adox.md), and [User](user-object-adox.md) objects. The **Name** property is read-only on [Catalog](catalog-object-adox.md), [Procedure](procedure-object-adox.md), and [View](view-object-adox.md) objects.

For read/write objects (**Column**, **Group**, **Key**, **Index**, **Table** and **User** objects), the default value is an empty string ("").


> [!NOTE]
> <P>For keys, this property is read-only on <STRONG>Key</STRONG> objects already appended to a collection.</P>




> [!NOTE]
> <P>For tables, this property is read-only for <STRONG>Table</STRONG> objects already appended to a collection.</P>


