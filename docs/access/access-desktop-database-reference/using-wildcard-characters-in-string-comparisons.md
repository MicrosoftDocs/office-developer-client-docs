---
title: Using Wildcard Characters in String Comparisons
TOCTitle: Using Wildcard Characters in String Comparisons
ms:assetid: 37dda2b8-c710-4f73-bb2a-76a1348c42fe
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192499(v=office.15)
ms:contentKeyID: 48544205
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Using Wildcard Characters in String Comparisons


**Applies to**: Access 2013 | Office 2013

Built-in pattern matching provides a versatile tool for making string comparisons. The following table shows the wildcard characters you can use with the **Like** operator and the number of digits or strings they match.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Character(s) in <em>pattern</em></p></th>
<th><p>Matches in <em>expression</em></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>? or _ (underscore)</p></td>
<td><p>Any single character</p></td>
</tr>
<tr class="even">
<td><p>* or %</p></td>
<td><p>Zero or more characters</p></td>
</tr>
<tr class="odd">
<td><p>#</p></td>
<td><p>Any single digit (0 – 9)</p></td>
</tr>
<tr class="even">
<td><p>[<em>charlist</em>]</p></td>
<td><p>Any single character in <em>charlist</em></p></td>
</tr>
<tr class="odd">
<td><p>[!<em>charlist</em>]</p></td>
<td><p>Any single character not in <em>charlist</em></p></td>
</tr>
</tbody>
</table>


You can use a group of one or more characters (*charlist*) enclosed in brackets (\[ \]) to match any single character in *expression,* and *charlist* can include almost any characters in the ANSI character set, including digits. You can use the special characters opening bracket (\[ ), question mark (?), number sign (\#), and asterisk (\*) to match themselves directly only if enclosed in brackets. You cannot use the closing bracket ( \]) within a group to match itself, but you can use it outside a group as an individual character.

In addition to a simple list of characters enclosed in brackets, *charlist* can specify a range of characters by using a hyphen (-) to separate the upper and lower bounds of the range. For example, using \[A-Z\] in *pattern* results in a match if the corresponding character position in *expression* contains any of the uppercase letters in the range A through Z. You can include multiple ranges within the brackets without delimiting the ranges. For example, \[a-zA-Z0-9\] matches any alphanumeric character.

It is important to note that the ANSI SQL wildcards (%) and (\_) are only available with Microsoft® Jet version 4.X and the Microsoft OLE DB Provider for Jet. They will be treated as literals if used through Microsoft Access or DAO.

Other important rules for pattern matching include the following:

  - An exclamation mark (\!) at the beginning of *charlist* means that a match is made if any character except those in *charlist* are found in *expression*. When used outside brackets, the exclamation mark matches itself.

  - You can use the hyphen (-) either at the beginning (after an exclamation mark if one is used) or at the end of *charlist* to match itself. In any other location, the hyphen identifies a range of ANSI characters.

  - When you specify a range of characters, the characters must appear in ascending sort order (A-Z or 0-100). \[A-Z\] is a valid pattern, but \[Z-A\] is not.

  - The character sequence \[ \] is ignored; it is considered to be a zero-length string ("").

