---
title: ConvertToString Method (RDS)
TOCTitle: ConvertToString Method (RDS)
ms:assetid: dc6381e4-98c8-badc-ad8c-87c70574a8a4
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250113(v=office.15)
ms:contentKeyID: 48548136
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ConvertToString Method (RDS)


**Applies to**: Access 2013 | Office 2013 

Converts a [Recordset](recordset-object-ado.md) to a MIME string that represents the recordset data.

## Syntax

*DataFactory*.ConvertToString(*Recordset*)

## Parameters

  - *DataFactory*

  - An object variable that represents an [RDSServer.DataFactory](datafactory-object-rdsserver.md) object.

  - *Recordset*

  - An object variable that represents a **Recordset** object.

## Remarks

With .asp files, use **ConvertToString** to embed the **Recordset** in an HTML page generated on the server to transport it to a client computer.

**ConvertToString** first loads the **Recordset** into the Cursor Service tables, and then generates a stream in MIME format.

On the client, Remote Data Service can convert the MIME string back into a fully functioning **Recordset**. It works well for handling fewer than 400 rows of data with no more than 1024 bytes width per row. You shouldn't use it for streaming BLOB data and large result sets over HTTP. No wire compression is performed on the string, so very large data sets will take considerable time to transport over HTTP when compared to the wire-optimized tablegram format defined and deployed by Remote Data Service as its native transport protocol format.


> [!NOTE]
> If you are using Active Server Pages to embed the resulting MIME string in a client HTML page, be aware that versions of VBScript earlier than version 2.0 limit the string's size to 32K. If this limit is exceeded, an error is returned. Keep the query scope relatively small when using MIME embedding via .asp files. To fix this, download the latest version of VBScript from the [Microsoft Download Center](https://www.microsoft.com/downloads/en/default.aspx).


