---
title: Stream Object (ADO)
TOCTitle: Stream Object (ADO)
ms:assetid: d49b1514-e0b4-0aca-d5c2-8266f3f4fe65
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250065(v=office.15)
ms:contentKeyID: 48547945
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Stream Object (ADO)


**Applies to**: Access 2013, Office 2013

Represents a stream of binary data or text.

## Remarks

In tree-structured hierarchies such as a file system or an e-mail system, a [Record](record-object-ado.md) may have a default binary stream of bits associated with it that contains the contents of the file or the e-mail. A **Stream** object can be used to manipulate fields or records containing these streams of data. A **Stream** object can be obtained in these ways:

  - From a URL pointing to an object (typically a file) containing binary or text data. This object can be a simple document, a **Record** object representing a structured document, or a folder.

  - By opening the default **Stream** object associated with a **Record** object. You can obtain the default stream associated with a **Record** object when the **Record** is opened, to eliminate a round-trip just to open the stream.

  - By instantiating a **Stream** object. These **Stream** objects can be used to store data for the purposes of your application. Unlike a **Stream** associated with a URL, or the default **Stream** of a **Record**, an instantiated **Stream** has no association with an underlying source by default.

With the methods and properties of a **Stream** object, you can do the following:

  - Open a **Stream** object from a **Record** or URL with the [Open](open-method-ado-stream.md) method.

  - Close a **Stream** with the [Close](close-method-ado.md) method.

  - Input bytes or text to a **Stream** with the [Write](write-method-ado.md) and [WriteText](writetext-method-ado.md) methods.

  - Read bytes from the **Stream** with the [Read](read-method-ado.md) and [ReadText](readtext-method-ado.md) methods.

  - Write any **Stream** data still in the ADO buffer to the underlying object with the [Flush](flush-method-ado.md) method.

  - Copy the contents of a **Stream** to another **Stream** with the [CopyTo](copyto-method-ado.md) method.

  - Control how lines are read from the source file with the [SkipLine](skipline-method-ado.md) method and the [LineSeparator](lineseparator-property-ado.md) property.

  - Determine the end of stream position with the [EOS](eos-property-ado.md) property and [SetEOS](seteos-method-ado.md) method.

  - Save and restore data in files with the [SaveToFile](savetofile-method-ado.md) and [LoadFromFile](loadfromfile-method-ado.md) methods.

  - Specify the character set used for storing the **Stream** with the [Charset](charset-property-ado.md) property.

  - Halt an asynchronous **Stream** operation with the [Cancel](cancel-method-ado.md) method.

  - Determine the number of bytes in a **Stream** with the [Size](https://msdn.microsoft.com/library/jj250128\(v=office.15\)) property.

  - Control the current position within a **Stream** with the [Position](position-property-ado.md) property.

  - Determine the type of data in a **Stream** with the [Type](type-property-ado-stream.md) property.

  - Determine the current state of the **Stream** (closed, open, or executing) with the [State](state-property-ado.md) property.

  - Specify the access mode for the **Stream** with the [Mode](mode-property-ado.md) property.


> [!NOTE]
> <P>URLs using the http scheme will automatically invoke the <A href="microsoft-ole-db-provider-for-internet-publishing.md">Microsoft OLE DB Provider for Internet Publishing</A>. For more information, see <A href="absolute-and-relative-urls.md">Absolute and Relative URLs</A>.</P>


