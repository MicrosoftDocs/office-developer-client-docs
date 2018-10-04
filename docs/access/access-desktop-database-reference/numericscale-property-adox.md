---
title: NumericScale Property (ADOX)
TOCTitle: NumericScale Property (ADOX)
ms:assetid: ebe73bdc-2570-f54a-3d2f-85a2a4634c9a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250197(v=office.15)
ms:contentKeyID: 48548501
ms.date: 09/18/2015
mtps_version: v=office.15
---

# NumericScale Property (ADOX)


**Applies to**: Access 2013 | Office 2013

Indicates the scale of a numeric value in the column.

## Settings and Return Values

Sets and returns a **Byte** value that is the scale of data values in the column when the [Type](https://msdn.microsoft.com/en-us/library/jj249169\(v=office.15\)) property is **adNumeric** or **adDecimal**. **NumericScale** is ignored for all other data types.

## Remarks

The default value is zero (0).

**NumericScale** is read-only for [Column](column-object-adox.md) objects already appended to a collection.

