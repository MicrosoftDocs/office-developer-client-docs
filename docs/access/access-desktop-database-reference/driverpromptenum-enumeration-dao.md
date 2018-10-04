---
title: DriverPromptEnum Enumeration (DAO)
TOCTitle: DriverPromptEnum Enumeration
ms:assetid: 8dda5e9f-a58f-a62d-eb49-5966d4a1e086
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff197361(v=office.15)
ms:contentKeyID: 48546266
ms.date: 09/18/2015
mtps_version: v=office.15
---

# DriverPromptEnum Enumeration (DAO)


_**Applies to:** Access 2013 | Office 2013_

Specifies if and when to prompt the user to establish a connection.

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
<td><p>dbDriverComplete</p></td>
<td><p>0</p></td>
<td><p>If the connection string provided includes the DSN keyword, the driver manager uses the string as provided in connect, otherwise it behaves as it does when <strong>dbDriverPrompt</strong> is specified.</p></td>
</tr>
<tr class="even">
<td><p>dbDriverCompleteRequired</p></td>
<td><p>3</p></td>
<td><p>(Default) Behaves like <strong>dbDriverComplete</strong> except the driver disables the controls for any information not required to complete the connection.</p></td>
</tr>
<tr class="odd">
<td><p>dbDriverNoPrompt</p></td>
<td><p>1</p></td>
<td><p>The driver manager uses the connection string provided in connect. If sufficient information is not provided, a trappable error is returned.</p></td>
</tr>
<tr class="even">
<td><p>dbDriverPrompt</p></td>
<td><p>2</p></td>
<td><p>The driver manager displays the <strong>ODBC Data Sources</strong> dialog box. The connection string used to establish the connection is constructed from the data source name (DSN) selected and completed by the user via the dialog boxes.</p></td>
</tr>
</tbody>
</table>

