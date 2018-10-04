---
title: Customization File Connect Section
TOCTitle: Customization File Connect Section
ms:assetid: 037abfb4-798d-4b09-6133-356969aee95c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ248802(v=office.15)
ms:contentKeyID: 48542985
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Customization File Connect Section


**Applies to**: Access 2013 | Office 2013

The default behavior of the handler is to deny all connections. The **connect** section specifies exceptions to that behavior. For example, if all the **connect** sections were absent or empty, then by default no connections could be made.

The **connect** section can contain:

  - A default access entry that specifies the default read and write operations allowed on this connection. If there is no default access entry in the section, the section will be ignored.

  - A new connection string that replaces the client connection string.

## Syntax

A default access entry is of the form:

    Access=accessRight

A replacement connection string entry is of the form:

    Connect=connectionString

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Part</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Connect</strong></p></td>
<td><p>A literal string that indicates this is a connection string entry.</p></td>
</tr>
<tr class="even">
<td><p><strong><em>connectionString</em></strong></p></td>
<td><p>A string that replaces the whole client connection string.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Access</strong></p></td>
<td><p>A literal string that indicates this is an access entry.</p></td>
</tr>
<tr class="even">
<td><p><strong><em>accessRight</em></strong></p></td>
<td><p>One of the following access rights:</p>
<p></p>
<ul>
<li><p><strong>NoAccess</strong> — User cannot access the data source.</p></li>
<li><p><strong>ReadOnly</strong> — User can read the data source.</p></li>
<li><p><strong>ReadWrite</strong> — User can read or write to the data source.</p></li>
</ul>
<p></p></td>
</tr>
</tbody>
</table>


If you want to allow any connection (in effect, disabling the default handler behavior), set the access entry in the **connect default** section to , and delete or comment out any other **connect** *identifier* section.

