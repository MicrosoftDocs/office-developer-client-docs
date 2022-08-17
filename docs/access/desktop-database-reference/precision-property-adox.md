---
title: Precision property (ADOX)
TOCTitle: Precision property (ADOX)
ms:assetid: 5d8ca497-572a-52e0-18aa-f82deaea0813
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249330(v=office.15)
ms:contentKeyID: 48545117
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Precision property (ADOX)


**Applies to**: Access 2013, Office 2013

Indicates the maximum precision of data values in the column.

## Settings and return values

Sets and returns a **Long** value that is the maximum precision of data values in the column when the [Type](/office/vba/access/concepts/miscellaneous/type-property-columnadox) property is a numeric type. **Precision** is ignored for all other data types.

## Remarks

The default value is zero (0).

This property is read-only for [Column](column-object-adox.md) objects already appended to a collection.

