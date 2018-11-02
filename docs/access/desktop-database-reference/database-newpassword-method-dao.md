---
title: Database.NewPassword method (DAO)
TOCTitle: NewPassword Method
ms:assetid: 01c1c454-d651-222c-225a-2b02734a1b7a
ms:mtpsurl: https://msdn.microsoft.com/library/Ff844754(v=office.15)
ms:contentKeyID: 48542941
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1052943
f1_categories:
- Office.Version=v15
---

# Database.NewPassword method (DAO)


**Applies to**: Access 2013, Office 2013

Changes the password of an existing Microsoft Access database engine database (Microsoft Access workspaces only).

## Syntax

*expression* .NewPassword(***bstrOld***, ***bstrNew***)

*expression* An expression that returns a **Database** object.

### Parameters

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Required/Optional</p></th>
<th><p>Data Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>bstrOld</p></td>
<td><p>Required</p></td>
<td><p><strong>String</strong></p></td>
<td><p>The current setting of the <strong>Password</strong> property of the <strong>Database</strong> object.</p></td>
</tr>
<tr class="even">
<td><p>bstrNew</p></td>
<td><p>Required</p></td>
<td><p><strong>String</strong></p></td>
<td><p>The new setting of the <strong>Password</strong> property of the <strong>Database</strong> object.</p>
<p><strong>NOTE</strong>Use strong passwords that combine upper- and lowercase letters, numbers, and symbols. Weak passwords don't mix these elements. Strong password: Y6dh!et5. Weak password: House27. Use a strong password that you can remember so that you don't have to write it down.</p>
</td>
</tr>
</tbody>
</table>


## Remarks

The bstrOld and bstrNew strings can be up to 20 characters long and can include any characters except the ASCII character 0 (null). To clear the password, use a zero-length string ("") for bstrNew.

Passwords are case-sensitive.

If a database has no password, the Microsoft Access database engine will automatically create one by passing a zero-length string ("") for the old password.


> [!IMPORTANT]
> If you lose your password, you can never open the database again.


