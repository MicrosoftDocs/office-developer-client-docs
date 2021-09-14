---
title: Formal shape grammar
TOCTitle: Formal shape grammar
ms:assetid: a3220569-8804-3dc3-7f9f-b4f8cdab1316
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249752(v=office.15)
ms:contentKeyID: 48546774
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Formal shape grammar

**Applies to**: Access 2013, Office 2013

This is the formal grammar for creating any shape command:

  - Required grammatical terms are text strings delimited by angle brackets ("\<\>").

  - Optional terms are delimited by square brackets ("\[ \]").

  - Alternatives are indicated by a virgule ("|").

  - Repeating alternatives are indicated by an ellipsis ("...").

  - *Alpha* indicates a string of alphabetical letters.

  - *Digit* indicates a string of numbers.

  - *Unicode-digit* indicates a string of unicode digits.

All other terms are literals.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Term</p></th>
<th><p>Definition</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;shape-command&gt;</p></td>
<td><p>SHAPE [&lt;table-exp&gt; [[AS] &lt;alias&gt;]][&lt;shape-action&gt;]</p></td>
</tr>
<tr class="even">
<td><p>&lt;table-exp&gt;</p></td>
<td><p>{&lt;provider-command-text&gt;} |<br />
(&lt;shape-command&gt;) |<br />
TABLE &lt;quoted-name&gt; |<br />
&lt;quoted-name&gt;</p></td>
</tr>
<tr class="odd">
<td><p>&lt;shape-action&gt;</p></td>
<td><p>APPEND &lt;aliased-field-list&gt; |</p>
<p>COMPUTE &lt;aliased-field-list&gt; [BY &lt;field-list&gt;]</p></td>
</tr>
<tr class="even">
<td><p>&lt;aliased-field-list&gt;</p></td>
<td><p>&lt;aliased-field&gt; [, &lt;aliased-field...&gt;]</p></td>
</tr>
<tr class="odd">
<td><p>&lt;aliased-field&gt;</p></td>
<td><p>&lt;field-exp&gt; [[AS] &lt;alias&gt;]</p></td>
</tr>
<tr class="even">
<td><p>&lt;field-exp&gt;</p></td>
<td><p>(&lt;relation-exp&gt;) |</p>
<p>&lt;calculated-exp&gt; |</p>
<p>&lt;aggregate-exp&gt; |</p>
<p>&lt;new-exp&gt;</p></td>
</tr>
<tr class="odd">
<td><p>&lt;relation_exp&gt;</p></td>
<td><p>&lt;table-exp&gt; [[AS] &lt;alias&gt;]</p>
<p>&lt;table-exp&gt; [[AS] &lt;alias&gt;]</p></td>
</tr>
<tr class="even">
<td><p>&lt;relation-cond-list&gt;</p></td>
<td><p>&lt;relation-cond&gt; [, &lt;relation-cond&gt;...]</p></td>
</tr>
<tr class="odd">
<td><p>&lt;relation-cond&gt;</p></td>
<td><p>&lt;field-name&gt; TO &lt;child-ref&gt;</p></td>
</tr>
<tr class="even">
<td><p>&lt;child-ref&gt;</p></td>
<td><p>&lt;field-name&gt; |</p>
<p>PARAMETER &lt;param-ref&gt;</p></td>
</tr>
<tr class="odd">
<td><p>&lt;param-ref&gt;</p></td>
<td><p>&lt;number&gt;</p></td>
</tr>
<tr class="even">
<td><p>&lt;field-list&gt;</p></td>
<td><p>&lt;field-name&gt; [, &lt;field-name&gt;]</p></td>
</tr>
<tr class="odd">
<td><p>&lt;aggregate-exp&gt;</p></td>
<td><p>SUM(&lt;qualified-field-name&gt;) |</p>
<p>AVG(&lt;qualified-field-name&gt;) |</p>
<p>MIN(&lt;qualified-field-name&gt;) |</p>
<p>MAX(&lt;qualified-field-name&gt;) |</p>
<p>COUNT(&lt;qualified-alias&gt; | &lt;qualified-name&gt;) |</p>
<p>STDEV(&lt;qualified-field-name&gt;) |</p>
<p>ANY(&lt;qualified-field-name&gt;)</p></td>
</tr>
<tr class="even">
<td><p>&lt;calculated-exp&gt;</p></td>
<td><p>CALC(&lt;expression&gt;)</p></td>
</tr>
<tr class="odd">
<td><p>&lt;qualified-field-name&gt;</p></td>
<td><p>&lt;alias&gt;.[&lt;alias&gt;...]&lt;field-name&gt;</p></td>
</tr>
<tr class="even">
<td><p>&lt;alias&gt;</p></td>
<td><p>&lt;quoted-name&gt;</p></td>
</tr>
<tr class="odd">
<td><p>&lt;field-name&gt;</p></td>
<td><p>&lt;quoted-name&gt; [[AS] &lt;alias&gt;]</p></td>
</tr>
<tr class="even">
<td><p>&lt;quoted-name&gt;</p></td>
<td><p>&quot;&lt;string&gt;&quot; |</p>
<p>'&lt;string&gt;' |</p>
<p>[&lt;string&gt;] |</p>
<p>&lt;name&gt;</p></td>
</tr>
<tr class="odd">
<td><p>&lt;qualified-name&gt;</p></td>
<td><p>alias[.alias...]</p></td>
</tr>
<tr class="even">
<td><p>&lt;name&gt;</p></td>
<td><p>alpha [ alpha | digit | _ | # | : | ...]</p></td>
</tr>
<tr class="odd">
<td><p>&lt;number&gt;</p></td>
<td><p>digit [digit...]</p></td>
</tr>
<tr class="even">
<td><p>&lt;new-exp&gt;</p></td>
<td><p>NEW &lt;field-type&gt; [(&lt;number&gt; [, &lt;number&gt;])]</p></td>
</tr>
<tr class="odd">
<td><p>&lt;field-type&gt;</p></td>
<td><p>An OLE DB or ADO data type.</p></td>
</tr>
<tr class="even">
<td><p>&lt;string&gt;</p></td>
<td><p>unicode-char [unicode-char...]</p></td>
</tr>
<tr class="odd">
<td><p>&lt;expression&gt;</p></td>
<td><p>A Visual Basic for Applications expression whose operands are other non-CALC columns in the same row.</p></td>
</tr>
</tbody>
</table>

