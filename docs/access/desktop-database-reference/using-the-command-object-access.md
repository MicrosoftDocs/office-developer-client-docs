---
title: Using the Command Object (Access)
TOCTitle: Using the Command Object
ms:assetid: dab6f0dd-1efa-3a5c-b192-c6d6afcaabfb
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250102(v=office.15)
ms:contentKeyID: 48548088
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Using the Command Object (Access)


**Applies to**: Access 2013 | Office 2013

After connecting to a data source, you need to execute requests against it to obtain result sets. ADO encapsulates this type of command functionality in the **Command** object.

You can use the **Command** object to request any type of operation from the provider, assuming that the provider can interpret the command string properly. A common operation for data providers is to query a database and return records in a **Recordset** object. **Recordset**s will be discussed later in this and other chapters; for now, think of them as tools to hold and view result sets. As with many ADO objects, depending on the functionality of the provider, some **Command** object collections, methods, or properties might generate errors when referenced.

It is not always necessary to create a **Command** object to execute a command against a data source. You can use the **Execute** method on the **Connection** object or the **Open** method on the **Recordset** object. However, you should use a **Command** object if you need to reuse a command in your code or if you need to pass detailed parameter information with your command. These scenarios are covered in more detail later in this chapter.

> [!NOTE]
> Certain Commands can return a result set as a binary stream or as a single Record rather than as a Recordset, if this is supported by the provider. Also, some Commands are not intended to return any result set at all (for example, a SQL Update query). This chapter will cover the most typical scenario, however: executing Commands that return results into a Recordset object. For more information about returning results into Records or Streams, see [Chapter 10: Records and Streams](chapter-10-records-and-streams.md).

This section includes the following topics:

- [Command Object Overview](command-object-overview.md)

- [Creating and Executing a Simple Command](creating-and-executing-a-simple-command.md)

- [Command Object Parameters](command-object-parameters.md)

- [Calling a Stored Procedure with a Command](calling-a-stored-procedure-with-a-command.md)

- [Named Commands](named-commands.md)
