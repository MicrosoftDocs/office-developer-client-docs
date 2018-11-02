---
title: Database.Synchronize method (DAO)
TOCTitle: Synchronize Method
ms:assetid: 5e716a4a-2430-8106-5c34-a02dd28bc4f6
ms:mtpsurl: https://msdn.microsoft.com/library/Ff194659(v=office.15)
ms:contentKeyID: 48545137
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1053357
f1_categories:
- Office.Version=v15
---

# Database.Synchronize method (DAO)


**Applies to**: Access 2013, Office 2013

Synchronizes two replicas. (Microsoft Access workspaces only).

## Syntax

*expression* .Synchronize(***DbPathName***, ***ExchangeType***)

*expression* A variable that represents a **Database** object.

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
<td><p>DbPathName</p></td>
<td><p>Required</p></td>
<td><p><strong>String</strong></p></td>
<td><p>The path to the target replica with which database will be synchronized.</p></td>
</tr>
<tr class="even">
<td><p>ExchangeType</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>A <strong><a href="synchronizetypeenum-enumeration-dao.md">SynchronizeTypeEnum</a></strong> constant indicating which direction to synchronize changes between the two databases.</p></td>
</tr>
</tbody>
</table>


## Remarks

You use **Synchronize** to exchange data and design changes between two databases. Design changes always happen first. Both databases must be at the same design level before they can exchange data. For example, an exchange of type **dbRepExportChanges** might cause design changes at a replica even though data changes flow only from the database to DbPathName.

The replica identified in DbPathName must be part of the same replica set. If both replicas have the same **ReplicaID** property setting or are Design Masters for two different replica sets, the synchronization fails.

When you synchronize two replicas over the Internet, you must use the **dbRepSyncInternet** constant. In this case, you specify a Uniform Resource Locator (URL) address for the DbPathName argument instead of specifying a local area network path.


> [!NOTE]
> You can't synchronize partial replicas with other partial replicas. See the [PopulatePartial](database-populatepartial-method-dao.md) method for more information.


