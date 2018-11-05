---
title: MoveRecord method (ADO)
TOCTitle: MoveRecord method (ADO)
ms:assetid: efc341a2-0e08-a838-5925-8d4c46377e48
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250217(v=office.15)
ms:contentKeyID: 48548588
ms.date: 09/18/2015
mtps_version: v=office.15
---

# MoveRecord method (ADO)

**Applies to**: Access 2013, Office 2013
 
Moves the entity represent by a [Record](record-object-ado.md) to another location.

## Syntax

*Record*.MoveRecord (*Source*, *Destination*, *UserName*, *Password*, *Options*, *Async*)

## Parameters

|Parameter|Description|
|:--------|:----------|
|*Source* |Optional. A **String** value that contains a URL identifying the **Record** to be moved. If *Source* is omitted or specifies an empty string, the object represented by this **Record** is moved. For example, if the **Record** represents a file, the contents of the file are moved to the location specified by *Destination*.|
|*Destination* |Optional. A **String** value that contains a URL specifying the location where *Source* will be moved.|
|*UserName* |Optional. A **String** value that contains the user ID that, if needed, authorizes access to *Destination*.|
|*Password* |Optional. A **String** that contains the password that, if needed, verifies *UserName*.|
|*Options* |Optional. A [MoveRecordOptionsEnum](moverecordoptionsenum.md) value whose default value is **adMoveUnspecified**. Specifies the behavior of this method.|
|*Async* |Optional. A **Boolean** value that, when **True**, specifies this operation should be asynchronous.|

## Return value

A **String** value. Typically, the value of *Destination* is returned. However, the exact value returned is provider-dependent.

## Remarks

The values of *Source* and *Destination* must not be identical; otherwise, a run-time error occurs. At least the server, path, and resource names must differ.

For files moved using the Internet Publishing Provider, this method updates all hypertext links in files being moved unless otherwise specified by *Options*. This method fails if *Destination* identifies an existing object (for example, a file or directory), unless **adMoveOverWrite** is specified.

> [!NOTE]
> Use the **adMoveOverWrite** option judiciously. For example, specifying this option when moving a file to a directory will delete the directory and replace it with the file.

Certain attributes of the **Record** object, such as the [ParentURL](parenturl-property-ado.md) property, will not be updated after this operation completes. Refresh the **Record** object's properties by closing the **Record**, then re-opening it with the URL of the location where the file or directory was moved.

If this **Record** was obtained from a [Recordset](recordset-object-ado.md), the new location of the moved file or directory will not be reflected immediately in the **Recordset**. Refresh the **Recordset** by closing and re-opening it.

> [!NOTE]
> URLs using the http scheme will automatically invoke the [Microsoft OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md). For more information, see [Absolute and relative URLs](absolute-and-relative-urls.md).


