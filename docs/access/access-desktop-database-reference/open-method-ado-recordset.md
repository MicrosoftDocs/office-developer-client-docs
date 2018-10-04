---
title: Open Method (ADO Recordset)
TOCTitle: Open Method (ADO Recordset)
ms:assetid: 87ef19a4-28e1-dec7-ed33-4ae500b9c460
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249591(v=office.15)
ms:contentKeyID: 48546119
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Open Method (ADO Recordset)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameters  
Remarks  

Opens a cursor.

## Syntax

*recordset*.Open*Source*, *ActiveConnection*, *CursorType*, *LockType*, *Options*

## Parameters

  - *Source*

  - Optional. A **Variant** that evaluates to a valid [Command](command-object-ado.md) object, an SQL statement, a table name, a stored procedure call, a URL, or the name of a file or [Stream](stream-object-ado.md) object containing a persistently stored [Recordset](recordset-object-ado.md).

  - *ActiveConnection*

  - Optional. Either a **Variant** that evaluates to a valid [Connection](connection-object-ado.md) object variable name, or a **String** that contains [ConnectionString](connectionstring-property-ado.md) parameters.

  - *CursorType*

  - Optional. A [CursorTypeEnum](cursortypeenum.md) value that determines the type of cursor that the provider should use when opening the **Recordset**. The default value is **adOpenForwardOnly**.

  - *LockType*

  - Optional. A [LockTypeEnum](locktypeenum.md) value that determines what type of locking (concurrency) the provider should use when opening the **Recordset**. The default value is **adLockReadOnly**.

  - *Options*

  - Optional. A **Long** value that indicates how the provider should evaluate the *Source* argument if it represents something other than a **Command** object, or that the **Recordset** should be restored from a file where it was previously saved. Can be one or more [CommandTypeEnum](commandtypeenum.md) or [ExecuteOptionEnum](executeoptionenum.md) values, which can be combined with a bitwise AND operator.


> [!NOTE]
> <P>If you open a <STRONG>Recordset</STRONG> from a <STRONG>Stream</STRONG> containing a persisted <STRONG>Recordset</STRONG>, using an <STRONG>ExecuteOptionEnum</STRONG> value of <STRONG>adAsyncFetchNonBlocking</STRONG> will not have an effect; the fetch will be synchronous and blocking.</P>



The **ExecuteOpenEnum** values of **adExecuteNoRecords** or **adExecuteStream** should not be used with **Open**.

## Remarks

The default cursor for an ADO **Recordset** is a forward-only, read-only cursor located on the server.

Using the **Open** method on a **Recordset** object opens a cursor that represents records from a base table, the results of a query, or a previously saved **Recordset**.

Use the optional *Source* argument to specify a data source using one of the following: a **Command** object variable, an SQL statement, a stored procedure, a table name, a URL, or a complete file path name. If *Source* is a file path name, it can be a full path ("c:\\dir\\file.rst"), a relative path ("..\\file.rst"), or a URL ("http://files/file.rst").

It is not a good idea to use the *Source* argument of the **Open** method to perform an action query that doesnt return records because there is no easy way to determine whether the call succeeded. The **Recordset** returned by such a query will be closed. Call the [Execute](https://msdn.microsoft.com/en-us/library/jj248785\(v=office.15\)) method of a **Command** object or the [Execute](https://msdn.microsoft.com/en-us/library/jj249832\(v=office.15\)) method of a **Connection** object instead to perform a query that, such as a SQL INSERT statement, that doesnt return records.

The *ActiveConnection* argument corresponds to the [ActiveConnection](activeconnection-property-ado.md) property and specifies in which connection to open the **Recordset** object. If you pass a connection definition for this argument, ADO opens a new connection using the specified parameters. After opening the **Recordset** with a client-side cursor (**CursorLocation** = **adUseClient**), you can change the value of this property to send updates to another provider. Or you can set this property to **Nothing** (in Microsoft Visual Basic) or NULL to disconnect the **Recordset** from any provider. Changing **ActiveConnection** for a server-side cursor generates an error, however.

For the other arguments that correspond directly to properties of a **Recordset** object (*Source*, *CursorType*, and *LockType*), the relationship of the arguments to the properties is as follows:

  - The property is read/write before the **Recordset** object is opened.

  - The property settings are used unless you pass the corresponding arguments when executing the **Open** method. If you pass an argument, it overrides the corresponding property setting, and the property setting is updated with the argument value.

  - After you open the **Recordset** object, these properties become read-only.


> [!NOTE]
> <P>The <STRONG>ActiveConnection</STRONG> property is read only for <STRONG>Recordset</STRONG> objects whose <A href="source-property-ado-recordset.md">Source</A> property is set to a valid <STRONG>Command</STRONG> object, even if the <STRONG>Recordset</STRONG> object isn't open.</P>



If you pass a **Command** object in the *Source* argument and also pass an *ActiveConnection* argument, an error occurs. The **ActiveConnection** property of the **Command** object must already be set to a valid **Connection** object or connection string.

If you pass something other than a **Command** object in the *Source* argument, you can use the *Options* argument to optimize evaluation of the *Source* argument. If the *Options* argument is not defined, you may experience diminished performance because ADO must make calls to the provider to determine if the argument is an SQL statement, a stored procedure, a URL, or a table name. If you know what *Source* type you're using, setting the *Options* argument instructs ADO to jump directly to the relevant code. If the *Options* argument does not match the *Source* type, an error occurs.

If you pass a **Stream** object in the *Source* argument, you should not pass information into the other arguments. Doing so will generate an error. The **ActiveConnection** information is not retained when a **Recordset** is opened from a **Stream**.

The default for the *Options* argument is **adCmdFile** if no connection is associated with the **Recordset**. This will typically be the case for persistently stored **Recordset** objects.

If the data source returns no records, the provider sets both the [BOF](bof-eof-properties-ado.md) and [EOF](bof-eof-properties-ado.md) properties to **True**, and the current record position is undefined. You can still add new data to this empty **Recordset** object if the cursor type allows it.

When you have concluded your operations over an open **Recordset** object, use the [Close](close-method-ado.md) method to free any associated system resources. Closing an object does not remove it from memory; you can change its property settings and use the **Open** method to open it again later. To completely eliminate an object from memory, set the object variable to *Nothing*.

Before the **ActiveConnection** property is set, call **Open** with no operands to create an instance of a **Recordset** created by appending fields to the **Recordset** [Fields](fields-collection-ado.md) collection.

If you have set the [CursorLocation](cursorlocation-property-ado.md) property to **adUseClient**, you can retrieve rows asynchronously in one of two ways. The recommended method is to set *Options* to **adAsyncFetch**. Alternatively, you can use the "Asynchronous Rowset Processing" dynamic property in the [Properties](properties-collection-ado.md) collection, but related retrieved events can be lost if you do not set the **Options** parameter to **adAsyncFetch**.


> [!NOTE]
> <P>Background fetching in the MS Remote provider is supported only through the <STRONG>Open</STRONG> method's <EM>Options</EM> parameter.</P>




> [!NOTE]
> <P>URLs using the http scheme will automatically invoke the <A href="microsoft-ole-db-provider-for-internet-publishing.md">Microsoft OLE DB Provider for Internet Publishing</A>. For more information, see <A href="absolute-and-relative-urls.md">Absolute and Relative URLs</A>.</P>


