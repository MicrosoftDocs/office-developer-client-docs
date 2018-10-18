---
title: RightsEnum (Access desktop database reference)
TOCTitle: RightsEnum
ms:assetid: 7647b9d5-5271-fdcf-489d-5a8beb931ca5
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249485(v=office.15)
ms:contentKeyID: 48545693
ms.date: 10/18/2018
mtps_version: v=office.15
---

# RightsEnum

**Applies to**: Access 2013 | Office 2013

Specifies the rights or permissions for a group or user on an object.

<br/>

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
<th><p>Value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>adRightCreate</strong></p></td>
<td><p>16384<br />
(&amp;H4000)</p></td>
<td><p>The user or group has permission to create new objects of this type.</p></td>
</tr>
<tr class="even">
<td><p><strong>adRightDelete</strong></p></td>
<td><p>65536<br />
(&amp;H10000)</p></td>
<td><p>The user or group has permission to delete data from an object. For objects such as <strong>Tables</strong>, the user has permission to delete data values from records.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adRightDrop</strong></p></td>
<td><p>256<br />
(&amp;H100)</p></td>
<td><p>The user or group has permission to remove objects from the catalog. For example, <strong>Tables</strong> can be deleted by a DROP TABLE SQL command.</p></td>
</tr>
<tr class="even">
<td><p><strong>adRightExclusive</strong></p></td>
<td><p>512<br />
(&amp;H200)</p></td>
<td><p>The user or group has permission to access the object exclusively.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adRightExecute</strong></p></td>
<td><p>536870912<br />
(&amp;H20000000)</p></td>
<td><p>The user or group has permission to execute the object.</p></td>
</tr>
<tr class="even">
<td><p><strong>adRightFull</strong></p></td>
<td><p>268435456<br />
(&amp;H10000000)</p></td>
<td><p>The user or group has all permissions on the object.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adRightInsert</strong></p></td>
<td><p>32768<br />
(&amp;H8000)</p></td>
<td><p>The user or group has permission to insert the object. For objects such as <strong>Tables</strong>, the user has permission to insert data into the table.</p></td>
</tr>
<tr class="even">
<td><p><strong>adRightMaximumAllowed</strong></p></td>
<td><p>33554432 (&amp;H2000000)</p></td>
<td><p>The user or group has the maximum number of permissions allowed by the provider. Specific permissions are provider-dependent.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adRightNone</strong></p></td>
<td><p>0</p></td>
<td><p>The user or group has no permissions for the object.</p></td>
</tr>
<tr class="even">
<td><p><strong>adRightRead</strong></p></td>
<td><p>-2147483648<br />
(&amp;H80000000)</p></td>
<td><p>The user or group has permission to read the object. For objects such as <a href="table-object-adox.md">Tables</a>, the user has permission to read the data in the table.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adRightReadDesign</strong></p></td>
<td><p>1024<br />
(&amp;H400)</p></td>
<td><p>The user or group has permission to read the design for the object.</p></td>
</tr>
<tr class="even">
<td><p><strong>adRightReadPermissions</strong></p></td>
<td><p>131072<br />
(&amp;H20000)</p></td>
<td><p>The user or group can view, but not change, the specific permissions for an object in the catalog.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adRightReference</strong></p></td>
<td><p>8192<br />
(&amp;H2000)</p></td>
<td><p>The user or group has permission to reference the object.</p></td>
</tr>
<tr class="even">
<td><p><strong>adRightUpdate</strong></p></td>
<td><p>1073741824<br />
(&amp;H40000000)</p></td>
<td><p>The user or group has permission to update the object. For objects such as <strong>Tables</strong>, the user has permission to update the data in the table.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adRightWithGrant</strong></p></td>
<td><p>4096<br />
(&amp;H1000)</p></td>
<td><p>The user or group has permission to grant permissions on the object.</p></td>
</tr>
<tr class="even">
<td><p><strong>adRightWriteDesign</strong></p></td>
<td><p>2048<br />
(&amp;H800)</p></td>
<td><p>The user or group has permission to modify the design for the object.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adRightWriteOwner</strong></p></td>
<td><p>524288<br />
(&amp;H80000)</p></td>
<td><p>The user or group has permission to modify the owner of the object.</p></td>
</tr>
<tr class="even">
<td><p><strong>adRightWritePermissions</strong></p></td>
<td><p>262144<br />
(&amp;H40000)</p></td>
<td><p>The user or group can modify the specific permissions for an object in the catalog.</p></td>
</tr>
</tbody>
</table>

