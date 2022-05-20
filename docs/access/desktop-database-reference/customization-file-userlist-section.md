---
title: Customization File UserList section
TOCTitle: Customization File UserList section
ms:assetid: b60ba3b0-37d4-bb59-d3cd-2ab44d178b8a
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249873(v=office.15)
ms:contentKeyID: 48547263
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Customization File UserList section


**Applies to**: Access 2013, Office 2013

The **userlist** section pertains to the **connect** section with the same section *identifier* parameter.

This section can contain a *user access entry*, which specifies access rights for the specified user and overrides the *default* *access entry* in the matching **connect** section.

## Syntax

A user access entry is of the form:

*userName***=*accessRights***

<table>
<colgroup>
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Part</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>userName</em></p></td>
<td><p>The <em>user name</em> of the person employing this connection. Valid user names are established with the IIS <strong>Service Manager</strong> dialog.</p></td>
</tr>
<tr class="even">
<td><p><strong><em>accessRights</em></strong></p></td>
<td><p>One of the following access rights:<br />
</p>
<ul>
<li><p><strong>NoAccess</strong> — User cannot access the data source.</p></li>
<li><p><strong>ReadOnly</strong> — User can read the data source.</p></li>
<li><p><strong>ReadWrite</strong> — User can read or write to the data source.</p></li>
</ul>
<p></p></td>
</tr>
</tbody>
</table>

