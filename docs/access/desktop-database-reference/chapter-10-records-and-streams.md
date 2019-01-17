---
title: 'Chapter 10: Records and streams'
TOCTitle: 'Chapter 10: Records and streams'
ms:assetid: 74862096-2273-3b61-f89c-06554ccf42cd
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249477(v=office.15)
ms:contentKeyID: 48545663
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# Chapter 10: Records and streams

**Applies to**: Access 2013, Office 2013

ADO currently provides the[Recordset](recordset-object-ado.md) object as the primary means of accessing information in data sources, such as relational databases. However, some providers support the [Record](record-object-ado.md) and [Stream](stream-object-ado.md) objects as alternative or complementary objects with which data from providers can be manipulated. For specifics on **Record** behavior, see your provider's documentation.

## Records

**Record** objects essentially function as one-row **Recordset**s. However, **Records** have limited functionality compared to **Recordsets** and they have different properties and methods.The source for the data in a **Record** object can be a command which returns one row of data from the provider. Using **Record** objects rather than **Recordset** objects to receive the results from a query that returns one row of data eliminates the overhead of instantiating the more complex **Recordset** object.

**Record** objects can serve another purpose, particularly with providers for data sources other than traditional relational databases, such as the [Microsoft OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md). Much of the information that must be processed exists, not as tables in databases, but as messages in electronic mail systems and files in modern file systems. The **Record** and **Stream** objects facilitate access to information stored in sources other than relational databases.

The **Record** object can represent and manage data such as directories and files in a file system or folders and messages in an email system. For these purposes, the source for the **Record** can be the current row of an open **Recordset**, an absolute URL, or a relative URL in conjunction with an open [Connection](connection-object-ado.md) object.

Typically, a **Recordset** can be used to represent a container or parent in a hierarchy such as a folder or directory. A **Record** can be used to return specific information about one node in the parent container, such as a file or document. The primary reason **Records** are used to represent this type of information is that these sources of data are heterogenous. This means that each **Record** may have a different set and number of fields. Traditional **Recordsets** containing rows from a database are homogenous, which means that each row has the same number and type of fields.

For more information about using the **Record** object for processing this heterogeneous data from providers such as the Internet Publishing Provider, see [Using ADO for Internet Publishing](using-ado-for-internet-publishing.md).

## Streams

The **Stream** object provides the means to read, write, and manage a stream of bytes. This byte stream may be text or binary and is limited in size only by system resources. Typically, ADO **Stream** objects are used for the following purposes:

- To contain the text or bytes that comprise a file or message, typically used with providers such as the Microsoft OLE DB Provider for Internet Publishing. For more information about this use of **Stream** objects, see [Using ADO for Internet Publishing](using-ado-for-internet-publishing.md).

A **Stream** object can be opened on:

- A simple file specified with a URL.

- A field of a **Record** or **Recordset** containing a **Stream** object.

- The default stream of a **Record** or **Recordset** object representing a directory or compound file.

- A resource field containing the URL of a simple file.

- No particular source at all. In this case, a **Stream** object is opened in memory. Data can be written to it and then saved in another **Stream** or file.

- A BLOB field in a **Recordset**.

This chapter covers the following topics:

- [Streams and persistence](streams-and-persistence.md)
- [Records and provider-supplied fields](records-and-provider-supplied-fields.md)
- [Absolute and relative URLs](absolute-and-relative-urls.md)
- [Using ADO for Internet publishing (ADO)](using-ado-for-internet-publishing.md)
