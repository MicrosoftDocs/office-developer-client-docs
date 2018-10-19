---
title: PageSize property (ADO)
TOCTitle: PageSize property (ADO)
ms:assetid: da56edd8-8947-aeff-2ef5-a8535c66575b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250099(v=office.15)
ms:contentKeyID: 48548079
ms.date: 09/18/2015
mtps_version: v=office.15
---

# PageSize property (ADO)


**Applies to**: Access 2013, Office 2013

Indicates how many records constitute one page in the [Recordset](recordset-object-ado.md).

## Settings and return values

Sets or returns a **Long** value that indicates how many records are on a page. The default is 10.

## Remarks

Use the **PageSize** property to determine how many records make up a logical page of data. Establishing a page size allows you to use the [AbsolutePage](absolutepage-property-ado.md) property to move to the first record of a particular page. This is useful in web server scenarios when you want to allow the user to page through data, viewing a certain number of records at a time.

This property can be set at any time, and its value will be used for calculating the location of the first record of a particular page.

