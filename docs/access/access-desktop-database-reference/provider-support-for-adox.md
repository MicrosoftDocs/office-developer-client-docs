---
title: Provider Support for ADOX
TOCTitle: Provider Support for ADOX
ms:assetid: 32ea3236-d69f-df94-1685-d8791aeb9e0f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249100(v=office.15)
ms:contentKeyID: 48544091
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Provider Support for ADOX


**Applies to**: Access 2013 | Office 2013

**In this article**  
Microsoft OLE DB Provider for SQL Server  
Microsoft OLE DB Provider for ODBC  
Microsoft OLE DB Provider for Oracle  

Certain features of ADOX are unsupported, depending upon your OLE DB data provider. ADOX is fully supported with the [OLE DB Provider for Microsoft Jet](microsoft-ole-db-provider-for-microsoft-jet.md). The unsupported features with the [Microsoft OLE DB Provider for SQL Server](microsoft-ole-db-provider-for-sql-server.md), the [Microsoft OLE DB Provider for ODBC](microsoft-ole-db-provider-for-odbc.md), or the [Microsoft OLE DB Provider for Oracle](microsoft-ole-db-provider-for-oracle.md) are listed below. ADOX is not supported by any other Microsoft OLE DB providers.

## Microsoft OLE DB Provider for SQL Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Object or Collection</p></th>
<th><p>Usage Restriction</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Catalog</strong> object</p></td>
<td><p>The <strong>Create</strong> method is not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tables</strong> collection</p></td>
<td><p>Properties are read/write prior to object creation, and read-only when referencing an existing object.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Views</strong> collection</p></td>
<td><p><strong>Views</strong> is not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Procedures</strong> collection</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Procedure</strong> object</p></td>
<td><p>The <strong>Command</strong> property is not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Keys</strong> collection</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Users</strong> collection</p></td>
<td><p><strong>Users</strong> is not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Groups</strong> collection</p></td>
<td><p><strong>Groups</strong> is not supported.</p></td>
</tr>
</tbody>
</table>


## Microsoft OLE DB Provider for ODBC

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Object or Collection</p></th>
<th><p>Usage Restriction</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Catalog</strong> object</p></td>
<td><p>The <strong>Create</strong> method is not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tables</strong> collection</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported. Properties are read/write prior to object creation, and read-only when referencing an existing object.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Procedures</strong> collection</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Procedure</strong> object</p></td>
<td><p>The <strong>Command</strong> property is not supported.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Indexes</strong> collection</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Keys</strong> collection</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Users</strong> collection</p></td>
<td><p><strong>Users</strong> is not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Groups</strong> collection</p></td>
<td><p><strong>Groups</strong> is not supported.</p></td>
</tr>
</tbody>
</table>


## Microsoft OLE DB Provider for Oracle

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Object or Collection</p></th>
<th><p>Usage Restriction</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Catalog</strong> object</p></td>
<td><p>The <strong>Create</strong> method is not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tables</strong> collection</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported. Properties are read/write prior to object creation, and read-only when referencing an existing object.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Views</strong> collection</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>View</strong> object</p></td>
<td><p>The <strong>Command</strong> property is not supported.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Procedures</strong> object</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Procedure</strong> object</p></td>
<td><p>The <strong>Command</strong> property is not supported.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Indexes</strong> collection</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Keys</strong> collection</p></td>
<td><p>The <strong>Append</strong> and <strong>Delete</strong> methods are not supported.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Users</strong> collection</p></td>
<td><p><strong>Users</strong> is not supported.</p></td>
</tr>
<tr class="even">
<td><p><strong>Groups</strong> collection</p></td>
<td><p><strong>Groups</strong> is not supported.</p></td>
</tr>
</tbody>
</table>

