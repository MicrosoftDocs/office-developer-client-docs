---
title: CopyRecord Method (ADO)
TOCTitle: CopyRecord Method (ADO)
ms:assetid: 724e4358-f216-8e47-5bab-c72770ece5a4
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249459(v=office.15)
ms:contentKeyID: 48545605
ms.date: 09/18/2015
mtps_version: v=office.15
---

# CopyRecord Method (ADO)


**Applies to**: Access 2013 | Office 2013

Copies a entity represented by a **Record** to another location.

## Syntax

*Record*.CopyRecord (*Source*, *Destination*, *UserName*, *Password*, *Options*, *Async*)

## Parameters

  - *Source*

  - Optional. A **String** value that contains a URL specifying the entity to be copied (for example, a file or directory). If *Source* is omitted or specifies an empty string, the file or directory represented by the current [Record](record-object-ado.md) will be copied.

  - *Destination*

  - Optional. A **String** value that contains a URL specifying the location where *Source* will be copied.

  - *UserName*

  - Optional. A **String** value that contains the user ID that, if needed, authorizes access to *Destination*.

  - *Password*

  - Optional. A **String** value that contains the password that, if needed, verifies *UserName*.

  - *Options*

  - Optional. A [CopyRecordOptionsEnum](copyrecordoptionsenum.md) value that has a default value of **adCopyUnspecified**. Specifies the behavior of this method.

  - *Async*

  - Optional. A **Boolean** value that, when **True**, specifies that this operation should be asynchronous.

<<<<<<< HEAD
## Return Value
=======
## Return value
>>>>>>> master

A **String** value that typically returns the value of *Destination*. However, the exact value returned is provider-dependent.

## Remarks

The values of *Source* and *Destination* must not be identical; otherwise, a run-time error occurs. At least one of the server, path, or resource names must differ.

All children (for example, subdirectories) of *Source* are copied recursively, unless **adCopyNonRecursive** is specified. In a recursive operation, *Destination* must not be a subdirectory of *Source*; otherwise, the operation will not complete.

This method fails if *Destination* identifies an existing entity (for example, a file or directory), unless **adCopyOverWrite** is specified.


> [!IMPORTANT]
> <P>Use the <STRONG>adCopyOverWrite</STRONG> option judiciously. For example, specifying this option when copying a file to a directory will <EM>delete</EM> the directory and replace it with the file.</P>




> [!NOTE]
<<<<<<< HEAD
> <P>URLs using the http scheme will automatically invoke the <A href="microsoft-ole-db-provider-for-internet-publishing.md">Microsoft OLE DB Provider for Internet Publishing</A>. For more information, see <A href="absolute-and-relative-urls.md">Absolute and Relative URLs</A>.</P>
=======
> URLs using the http scheme will automatically invoke the [Microsoft OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md). For more information, see [Absolute and relative URLs](absolute-and-relative-urls.md).
>>>>>>> master


