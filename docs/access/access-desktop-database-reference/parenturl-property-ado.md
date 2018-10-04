---
title: ParentURL Property (ADO)
TOCTitle: ParentURL Property (ADO)
ms:assetid: ec7ec476-6f9e-8486-fe02-74995975df5c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250200(v=office.15)
ms:contentKeyID: 48548517
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ParentURL Property (ADO)


_**Applies to:** Access 2013 | Office 2013_

Indicates an absolute URL string that points to the parent [Record](record-object-ado.md) of the current **Record** object.

## Return Value

Returns a **String** value that indicates the URL of the parent **Record**.

## Remarks

The **ParentURL** property depends upon the source used to open the **Record** object. For example, the **Record** may be opened with a source containing a relative path name of a directory referenced by the [ActiveConnection](activeconnection-property-ado.md) property.

Suppose "second" is a folder contained under "first". Open the **Record** object with the following:

    record.ActiveConnection = "http://first"
    record.Open "second"

Now, the value of the **ParentURL** property is **ParentURL** property is "http://first" , the same as **ActiveConnection**.

The source may also be an absolute URL such as, "http://first/second" . The **ParentURL** property is then "http://first" , the level above . The **ParentURL** property is then "http://first" , the level above "second" .

This property may be a null value if:

  - There is no parent for the current object; for example, if the **Record** object represents the root of a directory.

  - The **Record** object represents an entity that cannot be specified with a URL.

This property is read-only.


> [!NOTE]
> <P>This property is only supported by document source providers, such as the <A href="microsoft-ole-db-provider-for-internet-publishing.md">Microsoft OLE DB Provider for Internet Publishing</A>. For more information, see <A href="records-and-provider-supplied-fields.md">Records and Provider-Supplied Fields</A>.</P>




> [!NOTE]
> <P>URLs using the http scheme will automatically invoke the <A href="microsoft-ole-db-provider-for-internet-publishing.md">Microsoft OLE DB Provider for Internet Publishing</A>. For more information, see <A href="absolute-and-relative-urls.md">Absolute and Relative URLs</A>.</P>




> [!NOTE]
> <P>If the current record contains a data record from an ADO <STRONG>Recordset</STRONG>, accessing the <STRONG>ParentURL</STRONG> property causes a run-time error, indicating that no URL is possible.</P>


