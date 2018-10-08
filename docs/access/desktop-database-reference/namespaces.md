---
title: Namespaces (Access desktop database reference)
TOCTitle: Namespaces
ms:assetid: e39f003c-3d16-1fae-48c5-304593c41f2f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250158(v=office.15)
ms:contentKeyID: 48548318
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Namespaces


**Applies to**: Access 2013 | Office 2013

## Namespaces

The XML persistence format in ADO uses the following four namespaces.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Prefix</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>s</p></td>
<td><p>Refers to the &quot;XML-Data&quot; namespace containing the elements and attributes that define the schema of the current <strong>Recordset</strong>.</p></td>
</tr>
<tr class="even">
<td><p>dt</p></td>
<td><p>Refers to the data type definitions specification.</p></td>
</tr>
<tr class="odd">
<td><p>rs</p></td>
<td><p>Refers to the namespace containing elements and attributes specific to ADO <strong>Recordset</strong> properties and attributes.</p></td>
</tr>
<tr class="even">
<td><p>z</p></td>
<td><p>Refers to the schema of the current rowset.</p></td>
</tr>
</tbody>
</table>


A client should not add its own tags to these namespaces, as defined by the specification. For example, a client should not define a namespace as "urn:schemas-microsoft-com:rowset" and then write out something such as "rs:MyOwnTag." To learn more about namespaces, see [XML Namespaces](https://www.w3.org/tr/xml-names/).


> [!NOTE]
> <P>The ID for the schema tag must be "RowsetSchema," and the namespace used to refer to the schema of the current rowset must point to "#RowsetSchema."</P>



Note that the prefix of the namespace, that part to the right of the colon and to the left of the equal sign, is arbitrary.

```vb 
 
xmlns:rs="urn:schemas-microsoft-com:rowset" 
```

The user can define this to be any name as long as this name is consistently used throughout the XML document. ADO always writes out "s," "rs," "dt," and "z," but these prefix names are not hard-coded into the loading component.

## Namespaces

The XML persistence format in ADO uses the following four namespaces.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Prefix</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>s</p></td>
<td><p>Refers to the &quot;XML-Data&quot; namespace containing the elements and attributes that define the schema of the current <strong>Recordset</strong>.</p></td>
</tr>
<tr class="even">
<td><p>dt</p></td>
<td><p>Refers to the data type definitions specification.</p></td>
</tr>
<tr class="odd">
<td><p>rs</p></td>
<td><p>Refers to the namespace containing elements and attributes specific to ADO <strong>Recordset</strong> properties and attributes.</p></td>
</tr>
<tr class="even">
<td><p>z</p></td>
<td><p>Refers to the schema of the current rowset.</p></td>
</tr>
</tbody>
</table>


A client should not add its own tags to these namespaces, as defined by the specification. For example, a client should not define a namespace as "urn:schemas-microsoft-com:rowset" and then write out something such as "rs:MyOwnTag." To learn more about namespaces, see [XML Namespaces](https://www.w3.org/tr/xml-names/).


> [!NOTE]
> <P>The ID for the schema tag must be "RowsetSchema," and the namespace used to refer to the schema of the current rowset must point to "#RowsetSchema."</P>



Note that the prefix of the namespace, that part to the right of the colon and to the left of the equal sign, is arbitrary.

```vb 
 
xmlns:rs="urn:schemas-microsoft-com:rowset" 
```

The user can define this to be any name as long as this name is consistently used throughout the XML document. ADO always writes out "s," "rs," "dt," and "z," but these prefix names are not hard-coded into the loading component.

