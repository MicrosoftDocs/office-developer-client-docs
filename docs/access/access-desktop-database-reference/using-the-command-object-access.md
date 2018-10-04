---
title: Using the Command Object (Access)
TOCTitle: Using the Command Object
ms:assetid: dab6f0dd-1efa-3a5c-b192-c6d6afcaabfb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250102(v=office.15)
ms:contentKeyID: 48548088
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Using the Command Object (Access)


_**Applies to:** Access 2013 | Office 2013_

After connecting to a data source, you need to execute requests against it to obtain result sets. ADO encapsulates this type of command functionality in the **Command** object.

You can use the **Command** object to request any type of operation from the provider, assuming that the provider can interpret the command string properly. A common operation for data providers is to query a database and return records in a **Recordset** object. **Recordset**s will be discussed later in this and other chapters; for now, think of them as tools to hold and view result sets. As with many ADO objects, depending on the functionality of the provider, some **Command** object collections, methods, or properties might generate errors when referenced.

It is not always necessary to create a **Command** object to execute a command against a data source. You can use the **Execute** method on the **Connection** object or the **Open** method on the **Recordset** object. However, you should use a **Command** object if you need to reuse a command in your code or if you need to pass detailed parameter information with your command. These scenarios are covered in more detail later in this chapter.


> [!NOTE]
> <P>Certain <STRONG>Command</STRONG>s can return a result set as a binary stream or as a single <STRONG>Record</STRONG> rather than as a <STRONG>Recordset</STRONG>, if this is supported by the provider. Also, some <STRONG>Command</STRONG>s are not intended to return any result set at all (for example, a SQL Update query). This chapter will cover the most typical scenario, however: executing <STRONG>Command</STRONG>s that return results into a <STRONG>Recordset</STRONG> object. For more information about returning results into <STRONG>Record</STRONG>s or <STRONG>Stream</STRONG>s, see <A href="chapter-10-records-and-streams.md">Chapter 10: Records and Streams</A>.</P>


