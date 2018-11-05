---
title: Using ADO for Internet Publishing
TOCTitle: Using ADO for Internet Publishing
ms:assetid: 1e829783-fc12-e303-6f12-2df1ca96cb0f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248975(v=office.15)
ms:contentKeyID: 48543622
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Using ADO for Internet publishing


**Applies to**: Access 2013, Office 2013



[The OLE DB Provider for Internet Publishing](the-ole-db-provider-for-internet-publishing.md) shows a specific example of accessing heterogeneous data with ADO. While the examples in this section will be specific to using the Internet Publishing Provider, the principles demonstrated should be similar when using ADO with other providers to heterogeneous data, such as a provider to an email store.

## URLs

Uniform Resource Locators (URLs) can be used as an alternative to connection strings and command text to specify data sources and the location of files and directories. You can use URLs with the existing [Connection](connection-object-ado.md) and **Recordset** objects as well as with the **Record** and **Stream** objects.

For more information about using URLs, see [Absolute and Relative URLs](absolute-and-relative-urls.md).

## Record Fields

The distinguishing difference between heterogeneous data and homogeneous data is that for the former, each row of data, or **Record**, can have a different set of columns, or **Fields**. For homogeneous data, each row has the same set of columns. For more information about the fields specific to the Internet Publishing Provider, see [Records and Provider-Supplied Fields](records-and-provider-supplied-fields.md).

## Appending New Fields

Several ADO objects have been enhanced to work in conjunction with **Record** and **Stream** objects.

  - The [Fields](fields-collection-ado.md) collection [Append](append-method-ado.md) method, which creates and adds a [Field](field-object-ado.md) object to the collection, can also specify the value of the **Field**.

  - The [Update](update-method-ado.md) method finalizes the addition or deletion of fields to the collection.

  - As a shortcut and alternative to the **Append** method, you may create fields by simply assigning a value to an undefined or previously deleted field.

## See also

- [Internet Publishing Scenario topics](internet-publishing-scenario.md)