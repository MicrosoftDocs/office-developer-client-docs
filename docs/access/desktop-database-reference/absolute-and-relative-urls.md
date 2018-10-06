---
title: Absolute and Relative URLs
TOCTitle: Absolute and Relative URLs
ms:assetid: 79a1f793-7154-1c13-7dfe-a1b8cd64e1ea
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249501(v=office.15)
ms:contentKeyID: 48545774
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Absolute and Relative URLs

**Applies to**: Access 2013 | Office 2013 

A URL specifies the location of a target stored on a local or networked computer, such as a file, directory, HTML page, image, program, and so on*.* In this discussion, an *absolute URL* is of the form:

*scheme://server/path/resource*

where:

  - *scheme*

  - Specifies how the *resource* is to be accessed.

  - *server*

  - Specifies the name of the computer where the *resource* is located.

  - *path*

  - Specifies the sequence of directories leading to the target. If *resource* is omitted, the target is the last directory in *path*.

  - *resource*

  - If included, *resource* is the target, and is typically the name of a file. It may be a *simple file,* containing a single binary stream of bytes, or a *structured document,* containing one or more storages and binary streams of bytes.

An *absolute URL* contains all the information necessary to locate a resource.

A *relative URL* locates a resource using an absolute URL as a starting point. In effect, the "complete URL" of the target is specified by concatenating the absolute and relative URLs. A relative URL typically consists only of the *path*, and optionally, the *resource*, but no *scheme* or *server*.

## URL Scheme Registration

If a provider supports URLs, it will register for one or more URL schemes. This means that any URLs using this scheme will automatically invoke the registered provider. For example, the *http* scheme is registered to the [Microsoft OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md). ADO assumes all URLs prefixed with "http" represent Web folders or files to be used with the Internet Publishing Provider. For information about the schemes registered by your provider, see your provider documentation.

## Defining Context with a URL

One function of an open connection, represented by a [Connection](connection-object-ado.md) object, is to restrict subsequent operations to the data source represented by that connection. That is, the connection defines the context for subsequent operations.

With ADO 2.5, an absolute URL may also define a context. For example, when a [Record](record-object-ado.md) object is opened with an absolute URL, a **Connection** object is implicitly created to represent the resource specified by the URL.

An absolute URL that defines a context may be specified in the *ActiveConnection* parameter of the **Record** object [Open](open-method-ado-record.md) method. An absolute URL may also be specified as the value of the new "URL**=**" keyword in the **Connection** object [Open](open-method-ado-connection.md) method *ConnectionString* parameter, and the [Recordset](recordset-object-ado.md) object [Open](open-method-ado-recordset.md) method *ActiveConnection* parameter.

Context may also be defined with an open **Record** or **Recordset** object that represents a directory because these objects already have an implicitly or explicitly declared **Connection** object that specifies context.

## Scoped Operations

The context simultaneously defines a *scope* — that is, the directory and its subdirectories that may participate in subsequent operations. The **Record** object has several scoped methods, including [CopyRecord](copyrecord-method-ado.md), [MoveRecord](moverecord-method-ado.md), and [DeleteRecord](https://msdn.microsoft.com/library/jj249832\(v=office.15\)), that operate on a directory and all its subdirectories.

## Relative URLs as Command Text

A string specifying a command to be executed on the data source may be specified in the **Connection** object **Execute** method *CommandText* parameter, and the **Recordset** object **Open** method *Source* parameter.

A relative URL may be specified in the *CommandText* or *Source* parameter. The relative URL does not actually specify a command (such as an SQL command); it is merely specified in those parameters. In addition, the context of the active connection must be an absolute URL, and the *Option* parameter must be set to **adCmdTableDirect**.

For example, a **Recordset** could be opened on the Readme25.txt file of the Winnt/system32 directory like this:

```vb
recordset.Open "system32/Readme25.txt", "URL=https://YourServer/Winnt/",,,adCmdTableDirect 
```

The absolute URL in the connection string specifies the server (YourServer ) and the path () and the path (Winnt ). This URL also defines the context.

The relative URL in the command text uses the absolute URL as a starting point and specifies the remainder of the path (system32 ) and the file to open () and the file to open (Readme25.txt ).

The options field () indicates that the command type is a relative URL.

As another example, the following code will open a **Recordset** on the contents of the directory:

```vb
recordset.Open "", "URL=https://YourServer/Winnt/",,,adCmdTableDirect 
```

## OLE DB Provider-Supplied URL Schemes

The leading part of a fully-qualified URL is the *scheme* used to access the resource identified by the remainder of the URL. Examples are HTTP (HyperText Transfer Protocol) and FTP (File Transfer Protocol).

ADO supports OLE DB providers that recognize their own URL schemes. For example, the [Microsoft OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md)*,* which accesses "published" Windows 2000 files, recognizes the existing HTTP scheme.

