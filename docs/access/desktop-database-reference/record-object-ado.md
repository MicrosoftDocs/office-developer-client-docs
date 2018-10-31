---
title: Record Object (ADO)
TOCTitle: Record Object (ADO)
ms:assetid: 817aaf13-78d4-1134-aa94-997e92077c22
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249557(v=office.15)
ms:contentKeyID: 48545952
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Record Object (ADO)


**Applies to**: Access 2013 | Office 2013

Represents a row from a [Recordset](recordset-object-ado.md) or the data provider, or an object returned by a semi-structured data provider, such as a file or directory.

## Remarks

A **Record** object represents one row of data, and has some conceptual similarities with a one-row **Recordset**. Depending upon the capabilities of your provider, **Record** objects may be returned directly from your provider instead of a one-row **Recordset**, for example when an SQL query that selects only one row is executed. Or, a **Record** object can be obtained directly from a **Recordset** object. Or, a **Record** can be returned directly from a provider to semi-structured data, such as the Microsoft Exchange OLE DB provider.

You can view the fields associated with the **Record** object by way of the [Fields](fields-collection-ado.md) collection on the **Record** object. ADO allows object-valued columns including **Recordset**, **SafeArray**, and scalar values in the **Fields** collection of **Record** objects.

If the **Record** object represents a row in a **Recordset**, then it is possible to return to that original **Recordset** with the [Source](source-property-ado-record.md) property.

The **Record** object can also be used by semi-structured data providers such as the [Microsoft OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md), to model tree-structured namespaces. Each node in the tree is a **Record** object with associated columns. The columns can represent the attributes of that node and other relevant information. The **Record** object can represent both a leaf node and a non-leaf node in the tree structure. Non-leaf nodes have other nodes as their contents while leaf nodes do not have such contents. Leaf nodes typically contain binary streams of data while non-leaf nodes may also have a default binary stream associated with them. Properties on the **Record** object identify the type of node.

The **Record** object also represents an alternative way for navigating hierarchically organized data. A **Record** object may be created to represent the root of a specific sub-tree in a large tree structure and new **Record** objects may be opened to represent child nodes.

A resource (for example, a file or directory) can be uniquely identified by an absolute URL. A [Connection](connection-object-ado.md) object is implicitly created and set to the **Record** object when the **Record** is opened with an absolute URL. A **Connection** object may explicitly be set to the **Record** object via the [ActiveConnection](activeconnection-property-ado.md) property. The files and directories accessible via the **Connection** object define the *context* in which **Record** operations may occur.

Data modification and navigation methods on the **Record** object also accept a relative URL, which locates a resource using an absolute URL or the **Connection** object context as a starting point.

<<<<<<< HEAD

> [!NOTE]
> <P>URLs using the http scheme will automatically invoke the <A href="microsoft-ole-db-provider-for-internet-publishing.md">Microsoft OLE DB Provider for Internet Publishing</A>. For more information, see <A href="absolute-and-relative-urls.md">Absolute and Relative URLs</A>.</P>
=======
> [!NOTE]
> URLs using the http scheme will automatically invoke the [Microsoft OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md). For more information, see [Absolute and relative URLs](absolute-and-relative-urls.md).
>>>>>>> master



A **Connection** object is associated with each **Record** object. Therefore, **Record** object operations can be part of a transaction by invoking **Connection** object transaction methods.

The **Record** object does not support ADO events, and therefore will not respond to notifications.

With the methods and properties of a **Record** object, you can do the following:

  - Set or return the associated **Connection** object with the [ActiveConnection](activeconnection-property-ado.md) property.

  - Indicate access permissions with the [Mode](mode-property-ado.md) property.

  - Return the URL of the directory, if any, that contains the resource represented by the **Record** with the [ParentURL](parenturl-property-ado.md) property.

  - Indicate the absolute URL, relative URL, or **Recordset** from which the **Record** is derived with the [Source](source-property-ado-record.md) property.

  - Indicate the current status of the **Record** with the [State](state-property-ado.md) property.

  - Indicate the type of **Record** — *simple*, *collection*, or *structured document* — with the [RecordType](recordtype-property-ado.md) property.

  - Halt execution of an asynchronous operation with the [Cancel](cancel-method-ado.md) method.

  - Disassociate the **Record** from a data source with the [Close](close-method-ado.md) method.

  - Copy the file or directory represented by a **Record** to another location with the [CopyRecord](copyrecord-method-ado.md) method.

  - Delete the file, or directory and subdirectories, represented by a **Record** with the [DeleteRecord](deleterecord-method-ado.md) method.

  - Open a **Recordset** containing rows that represent the subdirectories and files of the entity represented by the **Record** with the [GetChildren](getchildren-method-ado.md) method.

  - Move (rename) the file, or directory and subdirectories, represented by a **Record** to another location with the [MoveRecord](moverecord-method-ado.md) method.

  - Associate the **Record** with an existing data source, or create a new file or directory with the [Open](open-method-ado-record.md) method.

