---
title: Records and provider-supplied fields
TOCTitle: Records and provider-supplied fields
ms:assetid: cde72d6a-b9b0-9636-581d-68239a3f522d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250022(v=office.15)
ms:contentKeyID: 48547776
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Records and provider-supplied fields

**Applies to**: Access 2013, Office 2013

When a [Record](record-object-ado.md) object is opened, its source can be the current row of an open [Recordset](recordset-object-ado.md), an absolute URL, or a relative URL in conjunction with an open [Connection](connection-object-ado.md) object.

If the **Record** is opened from a **Recordset**, the **Record** object [Fields](fields-collection-ado.md) collection will contain all the fields from the **Recordset**, plus any fields added by the underlying provider.

The provider may insert additional fields that serve as supplementary characteristics of the **Record**. As a result, a **Record** may have unique fields not in the **Recordset** as a whole or any **Record** derived from another row of the **Recordset**.

For example, all rows of a **Recordset** derived from an email data source might have columns such as From, To, and Subject. A **Record** derived from that **Recordset** will have the same fields. However, the **Record** may also have other fields unique to the particular message represented by that **Record**, such as Attachment and Cc (carbon copy).

Although the **Record** object and current row of the **Recordset** have the same fields, they are different because **Record** and **Recordset** objects have different methods and properties.

A field held in common by the **Record** and **Recordset** can be modified on either object. However, the field cannot be deleted on the **Record** object, although the underlying provider may support setting the field to null.

After the **Record** is opened, you can programmatically add fields. You can also delete fields you have added, but you cannot delete fields from the original **Recordset**.

You may also open the **Record** object directly from a URL. In this case, the fields added to the **Record** depend on the underlying provider. Currently, most providers add a set of fields that describe the entity represented by the **Record**. If the entity consists of a stream of bytes, such as a simple file, then a [Stream](stream-object-ado.md) object can usually be opened from the **Record**.

## Special Fields for Document Source Providers

A special class of providers, called *document source providers*, manages folders and documents. When a **Record** object represents a document or a **Recordset** object represents a folder of documents, the document source provider populates those objects with a unique set of fields that describe characteristics of the document instead of the actual document itself. Typically, one field contains a reference to the **Stream** that represents the document.

These fields constitute a resource **record** or **recordset** and are listed for the specific providers that support them in [Appendix A: Providers](appendix-a-providers.md).

Two constants index the **Fields** collection of a resource **Record** or **Recordset** to retrieve a pair of commonly used fields. The **Field** object [Value](value-property-ado.md) property returns the desired content.

  - The field accessed with the **adDefaultStream** constant contains a default stream associated with the **Record** or **Recordset** object. The provider assigns a default stream to an object.

  - The field accessed with the **adRecordURL** constant contains the absolute URL that identifies the document.

A document source provider does not support the [Properties](properties-collection-ado.md) collection of **Record** and **Field** objects. The content of the **Properties** collection is null for such objects.

A document source provider may add a provider-specific property such as **Datasource Type** to identify whether it is a document source provider. For more information about how to determine your type of provider, see your provider documentation.

## Resource Recordset Columns

A *resource recordset* consists of the following columns.

<table>
<colgroup>
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Column name</p></th>
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RESOURCE_PARSENAME</p></td>
<td><p>AdVarWChar</p></td>
<td><p>Read-only. Indicates the URL of the resource.</p></td>
</tr>
<tr class="even">
<td><p>RESOURCE_PARENTNAME</p></td>
<td><p>AdVarWChar</p></td>
<td><p>Read-only. Indicates the absolute URL of the parent record.</p></td>
</tr>
<tr class="odd">
<td><p>RESOURCE_ABSOLUTEPARSENAME</p></td>
<td><p>AdVarWChar</p></td>
<td><p>Read-only. Indicates the absolute URL of the resource, which is the concatenation of PARENTNAME and PARSENAME.</p></td>
</tr>
<tr class="even">
<td><p>RESOURCE_ISHIDDEN</p></td>
<td><p>AdBoolean</p></td>
<td><p>True if the resource is hidden. No rows will be returned unless the command that creates the rowset explicitly selects rows where RESOURCE_ISHIDDEN is True.</p></td>
</tr>
<tr class="odd">
<td><p>RESOURCE_ISREADONLY</p></td>
<td><p>AdBoolean</p></td>
<td><p>True if the resource is read-only. Attempts to open this resource with DBBINDFLAG_WRITE and will fail with DB_E_READONLY. This property may be edited even when the resource has only been opened for reading.</p></td>
</tr>
<tr class="even">
<td><p>RESOURCE_CONTENTTYPE</p></td>
<td><p>AdVarWChar</p></td>
<td><p>Indicates the likely use of the document — for example, a lawyer's brief. This may correspond to the Office template used to create the document.&quot;&quot;</p></td>
</tr>
<tr class="odd">
<td><p>RESOURCE_CONTENTCLASS</p></td>
<td><p>AdVarWChar</p></td>
<td><p>Indicates the MIME type of the document, indicating the format such as &quot;text/html&quot;.'</p></td>
</tr>
<tr class="even">
<td><p>RESOURCE_CONTENTLANGUAGE</p></td>
<td><p>AdVarWChar</p></td>
<td><p>Indicates the language in which the content is stored.</p></td>
</tr>
<tr class="odd">
<td><p>RESOURCE_CREATIONTIME</p></td>
<td><p>adFileTime</p></td>
<td><p>Read-only. Indicates a FILETIME structure containing the time the resource was created. The time is reported in Coordinated Universal Time (UTC) format.</p></td>
</tr>
<tr class="even">
<td><p>RESOURCE_LASTACCESSTIME</p></td>
<td><p>AdFileTime</p></td>
<td><p>Read-only. Indicates a FILETIME structure containing the time that the resource was last accessed. The time is in UTC format. The FILETIME members are zero if the provider does not support this time member.</p></td>
</tr>
<tr class="odd">
<td><p>RESOURCE_LASTWRITETIME</p></td>
<td><p>AdFileTime</p></td>
<td><p>Read-only. Indicates a FILETIME structure containing the time that the resource was last written. The time is in UTC format. The FILETIME members are zero if the provider does not support this time member.</p></td>
</tr>
<tr class="even">
<td><p>RESOURCE_STREAMSIZE</p></td>
<td><p>asUnsignedBigInt</p></td>
<td><p>Read-only. Indicates the size of the resource's default stream, in bytes.</p></td>
</tr>
<tr class="odd">
<td><p>RESOURCE_ISCOLLECTION</p></td>
<td><p>AdBoolean</p></td>
<td><p>Read-only. True if the resource is a collection, such as a directory. False if the resource is a simple file.</p></td>
</tr>
<tr class="even">
<td><p>RESOURCE_ISSTRUCTUREDDOCUMENT</p></td>
<td><p>AdBoolean</p></td>
<td><p>True if the resource is a structured document. False if the resource is not a structured document. It could be a collection or a simple file.</p></td>
</tr>
<tr class="odd">
<td><p>DEFAULT_DOCUMENT</p></td>
<td><p>AdVarWChar</p></td>
<td><p>Read-only. Indicates that this resource contains a URL to the default simple document of a folder or a structured document. Used when the default stream is requested from a resource. This property is blank for a simple file.</p></td>
</tr>
<tr class="even">
<td><p>CHAPTERED_CHILDREN</p></td>
<td><p>AdChapter</p></td>
<td><p>Read-only. Optional. Indicates the chapter of the rowset containing the children of the resource. (The <em>OLE DB Provider for Internet Publishing</em> does not use this column.)</p></td>
</tr>
<tr class="odd">
<td><p>RESOURCE_DISPLAYNAME</p></td>
<td><p>AdVarWChar</p></td>
<td><p>Read-only. Indicates the display name of the resource.</p></td>
</tr>
<tr class="even">
<td><p>RESOURCE_ISROOT</p></td>
<td><p>AdBoolean</p></td>
<td><p>Read-only. True if the resource is the root of a collection or structured document.</p></td>
</tr>
</tbody>
</table>

