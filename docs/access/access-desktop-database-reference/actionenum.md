---
title: ActionEnum
TOCTitle: ActionEnum
ms:assetid: 225024c1-9088-b532-2a23-04c1aaaaa892
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ248998(v=office.15)
ms:contentKeyID: 48543704
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ActionEnum


_**Applies to:** Access 2013 | Office 2013_

Specifies the type of action to be performed when [SetPermissions](setpermissions-method-adox.md) is called.

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
<td><p><strong>adAccessDeny</strong></p></td>
<td><p>3</p></td>
<td><p>The group or user will be denied the specified permissions.</p></td>
</tr>
<tr class="even">
<td><p><strong>adAccessGrant</strong></p></td>
<td><p>1</p></td>
<td><p>The group or user will have at least the requested permissions.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adAccessRevoke</strong></p></td>
<td><p>4</p></td>
<td><p>Any explicit access rights the group or user has will be revoked.</p></td>
</tr>
<tr class="even">
<td><p><strong>adAccessSet</strong></p></td>
<td><p>2</p></td>
<td><p>The group or user will have exactly the requested permissions.</p></td>
</tr>
</tbody>
</table>

