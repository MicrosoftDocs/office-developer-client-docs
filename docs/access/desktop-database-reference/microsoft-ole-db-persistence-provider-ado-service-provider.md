---
title: Microsoft OLE DB Persistence Provider (ADO Service Provider)
TOCTitle: Microsoft OLE DB Persistence Provider (ADO Service Provider)
ms:assetid: 22e41769-36eb-5a88-05ed-870938657624
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249007(v=office.15)
ms:contentKeyID: 48543719
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Microsoft OLE DB Persistence Provider (ADO Service Provider)


**Applies to**: Access 2013, Office 2013 

The Microsoft OLE DB Persistence Provider enables you to save a [Recordset](recordset-object-ado.md) object into a file, and later restore that **Recordset** object from the file. Schema information, data, and pending changes are preserved.

You can save the **Recordset** in either the proprietary Advanced Data Table Gram (ADTG) format, or the open Extensible Markup Language (XML) format.

## Provider Keyword

To invoke this provider, specify the following keyword and value in the connection string.

```vb 
 
"Provider=MSPersist" 
```

## Errors

The following errors issued by this provider can be detected in your application.

<table>
<colgroup>
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>E_BADSTREAM</p></td>
<td><p>The file opened does not have a valid format (that is, the format is not ADTG or XML).</p></td>
</tr>
<tr class="even">
<td><p>E_CANTPERSISTROWSET</p></td>
<td><p>The <strong>Recordset</strong> object saved has characteristics that prevent it from being stored.</p></td>
</tr>
</tbody>
</table>


## Remarks

The Microsoft OLE DB Persistence Provider exposes no dynamic properties.

Currently, only parameterized hierarchical **Recordset** objects cannot be saved.

For more information about persistently storing **Recordset** objects, see [Recordset Persistence](more-about-recordset-persistence.md).

When a stream is used to open a **Recordset**, there should be no parameters specified other than the *Source* parameter of the **Open** method.

