---
title: PermissionEnum Enumeration (DAO)
TOCTitle: PermissionEnum Enumeration
ms:assetid: dcce9940-f8a7-e915-1b69-05c341bea8cd
ms:mtpsurl: https://msdn.microsoft.com/library/Ff835373(v=office.15)
ms:contentKeyID: 48548147
ms.date: 09/18/2015
mtps_version: v=office.15
---

# PermissionEnum Enumeration (DAO)


**Applies to**: Access 2013, Office 2013

Used with the **Permissions** property to specify the type of permissions.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>dbSecCreate</p></td>
<td><p>1</p></td>
<td><p>The user can create new documents (not valid for Document objects).</p></td>
</tr>
<tr class="even">
<td><p>dbSecDBAdmin</p></td>
<td><p>8</p></td>
<td><p>The user can replicate a database and change the database password (not valid for Document objects).</p></td>
</tr>
<tr class="odd">
<td><p>dbSecDBCreate</p></td>
<td><p>1</p></td>
<td><p>The user can create new databases. This option is valid only on the Databases container in the workgroup information file (Systen.mdw). This constant is not valid for Document objects.</p></td>
</tr>
<tr class="even">
<td><p>dbSecDBExclusive</p></td>
<td><p>4</p></td>
<td><p>The user has exclusive access to the database.</p></td>
</tr>
<tr class="odd">
<td><p>dbSecDBOpen</p></td>
<td><p>2</p></td>
<td><p>The user can open the database.</p></td>
</tr>
<tr class="even">
<td><p>dbSecDelete</p></td>
<td><p>65536</p></td>
<td><p>The user can delete the object.</p></td>
</tr>
<tr class="odd">
<td><p>dbSecDeleteData</p></td>
<td><p>128</p></td>
<td><p>The user can delete records.</p></td>
</tr>
<tr class="even">
<td><p>dbSecFullAccess</p></td>
<td><p>1048575</p></td>
<td><p>The user has full access to the object.</p></td>
</tr>
<tr class="odd">
<td><p>dbSecInsertData</p></td>
<td><p>32</p></td>
<td><p>The user can add records.</p></td>
</tr>
<tr class="even">
<td><p>dbSecNoAccess</p></td>
<td><p>0</p></td>
<td><p>The user does not have access to the object (not valid for Document objects).</p></td>
</tr>
<tr class="odd">
<td><p>dbSecReadDef</p></td>
<td><p>4</p></td>
<td><p>The user can read the table definition, including column and index information.</p></td>
</tr>
<tr class="even">
<td><p>dbSecReadSec</p></td>
<td><p>131072</p></td>
<td><p>The user can read the object's security-related information.</p></td>
</tr>
<tr class="odd">
<td><p>dbSecReplaceData</p></td>
<td><p>64</p></td>
<td><p>The user can modify records.</p></td>
</tr>
<tr class="even">
<td><p>dbSecRetrieveData</p></td>
<td><p>20</p></td>
<td><p>The user can retrieve data from the Document object.</p></td>
</tr>
<tr class="odd">
<td><p>dbSecWriteDef</p></td>
<td><p>65548</p></td>
<td><p>The user can modify or delete the table definition, including column and index information.</p></td>
</tr>
<tr class="even">
<td><p>dbSecWriteOwner</p></td>
<td><p>524288</p></td>
<td><p>The user can change the Owner property setting.</p></td>
</tr>
<tr class="odd">
<td><p>dbSecWriteSec</p></td>
<td><p>262144</p></td>
<td><p>The user can alter access permissions.</p></td>
</tr>
</tbody>
</table>

