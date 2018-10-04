---
title: Understanding the Customization File
TOCTitle: Understanding the Customization File
ms:assetid: 98fd5ec1-d5bd-cdd2-5eb5-9a1682fbed79
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249686(v=office.15)
ms:contentKeyID: 48546507
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Understanding the Customization File


_**Applies to:** Access 2013 | Office 2013_

Each section header in the customization file consists of square brackets (**\[\]**) containing a type and parameter. The four section types are indicated by the literal strings **connect**, **sql**, **userlist**, or **logs**. The parameter is the literal string, the default, a user-specified identifier, or nothing.

Therefore, each section is marked with one of the following section headers:

``` 
 
[ connect   default     ]
[ connect   identifier  ]
[ sql       default     ]
[ sql       identifier  ]
[ userlist  identifier  ]
[ logs                  ]
```

The section headers have the following parts.

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
<td><p><strong>connect</strong></p></td>
<td><p>A literal string that modifies a connection string.</p></td>
</tr>
<tr class="even">
<td><p><strong>sql</strong></p></td>
<td><p>A literal string that modifies a command string.</p></td>
</tr>
<tr class="odd">
<td><p><strong>userlist</strong></p></td>
<td><p>A literal string that modifies the access rights of a specific user.</p></td>
</tr>
<tr class="even">
<td><p><strong>logs</strong></p></td>
<td><p>A literal string that specifies a log file recording operational errors.</p></td>
</tr>
<tr class="odd">
<td><p><strong>default</strong></p></td>
<td><p>A literal string that is used if no identifier is specified or found.</p></td>
</tr>
<tr class="even">
<td><p><em>identifier</em></p></td>
<td><p>A string that matches a string in the <strong>connect</strong> or <strong>command</strong> string.</p>
<p></p>
<ul>
<li><p>Use this section if the section header contains <strong>connect</strong> and the identifier string is found in the connection string.</p></li>
<li><p>Use this section if the section header contains <strong>sql</strong> and the identifier string is found in the command string.</p></li>
<li><p>Use this section if the section header contains <strong>userlist</strong> and the identifier string matches a <strong>connect</strong> section identifier.</p></li>
</ul>
<p></p></td>
</tr>
</tbody>
</table>


The **DataFactory** calls the handler, passing client parameters. The handler searches for whole strings in the client parameters that match identifiers in the appropriate section headers. If a match is found, the contents of that section are applied to the client parameter.

A particular section is used under the following circumstances:

  - A **connect** section is used if the value part of the client connect string keyword, "**Data Source=***value*", matches a **connect** section identifier*.*

  - An **sql** section is used if the client command string contains a string that matches an **sql** section identifier.

  - A **connect** or **sql** section with a default parameter is used if there is no matching identifier.

  - A **userlist** section is used if the **userlist** section identifier matches a **connect** section identifier. If there is a match, the contents of the **userlist** section are applied to the connection governed by the **connect** section.

  - If the string in a connection or command string does not match the identifier in any **connect** or **sql** section header, and there is no **connect** or **sql** section header with a default parameter, then the client string is used without modification.

  - The **logs** section is used whenever the **DataFactory** is in operation.

