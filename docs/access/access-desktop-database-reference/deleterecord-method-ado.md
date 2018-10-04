---
title: DeleteRecord Method (ADO)
TOCTitle: DeleteRecord Method (ADO)
ms:assetid: ba71187f-e580-bba8-f41b-bedfa0bc2b04
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249895(v=office.15)
ms:contentKeyID: 48547370
ms.date: 09/18/2015
mtps_version: v=office.15
---

# DeleteRecord Method (ADO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Parameters  
Remarks  

Deletes a the entity represented by a [Record](record-object-ado.md).

## Syntax

*Record*.**DeleteRecord***Source*, *Async*

## Parameters

  - *Source*

  - Optional. A **String** value that contains a URL identifying the entity (for example, the file or directory) to be deleted. If *Source* is omitted or specifies an empty string, the entity represented by the current [Record](record-object-ado.md) is deleted. If the Record is a collection record ([RecordType](recordtype-property-ado.md) of **adCollectionRecord**, such as a directory) all children (for example, subdirectories) will also be deleted.

  - *Async*

  - Optional. A **Boolean** value that, when **True**, specifies that the delete operation is asynchronous.

## Remarks

Operations on the object represented by this **Record** may fail after this method completes. After calling **DeleteRecord**, the **Record** should be closed because the behavior of the **Record** may become unpredictable depending upon when the provider updates the **Record** with the data source.

If this **Record** was obtained from a [Recordset](recordset-object-ado.md), then the results of this operation will not be reflected immediately in the **Recordset**. Refresh the **Recordset** by closing and re-opening it, or by executing the **Recordset** [Requery](requery-method-ado.md), or [Update](update-method-ado.md) and [Resync](resync-method-ado.md) methods.


> [!NOTE]
> <P>URLs using the http scheme will automatically invoke the <A href="microsoft-ole-db-provider-for-internet-publishing.md">Microsoft OLE DB Provider for Internet Publishing</A>. For more information, see <A href="absolute-and-relative-urls.md">Absolute and Relative URLs</A>.</P>


