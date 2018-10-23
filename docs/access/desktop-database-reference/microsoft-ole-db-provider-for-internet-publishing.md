---
title: Microsoft OLE DB Provider for Internet Publishing
TOCTitle: Microsoft OLE DB Provider for Internet Publishing
ms:assetid: 5d1e8db5-dabb-0914-e11e-e2eac72bfa77
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249327(v=office.15)
ms:contentKeyID: 48545100
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Microsoft OLE DB Provider for Internet Publishing

**Applies to**: Access 2013, Office 2013

The Microsoft OLE DB Provider for Internet Publishing allows ADO to access resources served by Microsoft FrontPage or Microsoft Internet Information Server. Resources include web source files such as HTML files, or Windows 2000 web folders.

## Connection String Parameters

To connect to this provider, set the *Provider* argument of the [ConnectionString](connectionstring-property-ado.md) property to:

```vb 
 
MSDAIPP.DSO 
```

This value can also be set or read using the [Provider](provider-property-ado.md) property.

## Typical Connection String

A typical connection string for this provider is:

```vb 
 
"Provider=MSDAIPP.DSO;Data Source=ResourceURL;User ID=userName;Password=userPassword;" 
```

\-or-

```vb 
 
"URL=ResourceURL;User ID=userName;Password=userPassword;" 
```

The string consists of these keywords:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Provider</strong></p></td>
<td><p>Specifies the OLE DB Provider for Internet Publishing.</p></td>
</tr>
<tr class="even">
<td><p><strong>Data Source</strong> -or- <strong>URL</strong></p></td>
<td><p>Specifies the URL of a file or directory published in a Web Folder.</p></td>
</tr>
<tr class="odd">
<td><p><strong>User ID</strong></p></td>
<td><p>Specifies the user name.</p></td>
</tr>
<tr class="even">
<td><p><strong>Password</strong></p></td>
<td><p>Specifies the user password.</p></td>
</tr>
</tbody>
</table>


If you set the *ResourceURL* value from the "URL=" in the connection string to an invalid value, by default the Internet Publishing Provider raises a dialog box to prompt for a valid value. This is undesirable behavior for a component in the middle tier of an application, because it suspends program execution until the dialog box is cleared and the client appears to freeze because it has not received a response from the component.


> [!NOTE]
> <P>If MSDAIPP.DSO is explicitly specified as the value of the provider, either with the <EM>Provider</EM> connection string keyword or the <STRONG>Provider</STRONG> property, you cannot use "URL=" in the connection string. If you do, an error will occur. Instead, simply specify the URL as shown in the topic <A href="the-ole-db-provider-for-internet-publishing.md">Using ADO with the OLE DB Provider for Internet Publishing</A>.</P>


