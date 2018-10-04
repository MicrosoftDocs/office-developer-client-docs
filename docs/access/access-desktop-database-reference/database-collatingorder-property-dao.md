---
title: Database.CollatingOrder Property (DAO)
TOCTitle: CollatingOrder Property
ms:assetid: 7f6c35bf-e5f9-8423-608e-bc072ca09141
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff196459(v=office.15)
ms:contentKeyID: 48545901
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Database.CollatingOrder Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

Returns a value that specifies the sequence of the sort order in text for string comparison or sorting (Microsoft Access workspaces only). Read-only **Long**.

## Syntax

*expression* .CollatingOrder

*expression* A variable that represents a **Database** object.

## Remarks

The return value is a **Long** value or constant that can be one of the following values.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
<th><p>Sort order</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>dbSortGeneral</strong></p></td>
<td><p>General (English, French, German, Portuguese, Italian, and Modern Spanish)</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortArabic</strong></p></td>
<td><p>Arabic</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortChineseSimplified</strong></p></td>
<td><p>Simplified Chinese</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortChineseTraditional</strong></p></td>
<td><p>Traditional Chinese</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortCyrillic</strong></p></td>
<td><p>Russian</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortCzech</strong></p></td>
<td><p>Czech</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortDutch</strong></p></td>
<td><p>Dutch</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortGreek</strong></p></td>
<td><p>Greek</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortHebrew</strong></p></td>
<td><p>Hebrew</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortHungarian</strong></p></td>
<td><p>Hungarian</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortIcelandic</strong></p></td>
<td><p>Icelandic</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortJapanese</strong></p></td>
<td><p>Japanese</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortKorean</strong></p></td>
<td><p>Korean</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortNeutral</strong></p></td>
<td><p>Neutral</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortNorwDan</strong></p></td>
<td><p>Norwegian or Danish</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortPDXIntl</strong></p></td>
<td><p>Paradox International</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortPDXNor</strong></p></td>
<td><p>Paradox Norwegian or Danish</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortPDXSwe</strong></p></td>
<td><p>Paradox Swedish or Finnish</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortPolish</strong></p></td>
<td><p>Polish</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortSlovenian</strong></p></td>
<td><p>Slovenian</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortSpanish</strong></p></td>
<td><p>Spanish</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortSwedFin</strong></p></td>
<td><p>Swedish or Finnish</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortThai</strong></p></td>
<td><p>Thai</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSortTurkish</strong></p></td>
<td><p>Turkish</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbSortUndefined</strong></p></td>
<td><p>Undefined or unknown</p></td>
</tr>
</tbody>
</table>


The **CollatingOrder** property setting corresponds to the locale argument of the **CreateDatabase** method when the database was created or the **CompactDatabase** method when the database was most recently compacted.

Check the **CollatingOrder** property setting of a **Database** or **Field** object to determine the string comparison method for the database or field. You can set the **CollatingOrder** property of a new, unappended **Field** object if you want the setting of the **Field** object to differ from that of the **Database** object that contains it.

