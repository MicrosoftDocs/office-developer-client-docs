---
title: URL Property (RDS - Access desktop database reference)
TOCTitle: URL Property (RDS)
ms:assetid: 722765dc-f89c-0131-73b1-69c56a795546
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249457(v=office.15)
ms:contentKeyID: 48545603
ms.date: 09/18/2015
mtps_version: v=office.15
---

# URL Property (RDS)


**Applies to**: Access 2013 | Office 2013



Indicates a string that contains a relative or absolute URL.

You can set the **URL** property at design time in the [DataControl](datacontrol-object-rds.md) object's OBJECT tag, or at run time in scripting code.

## Syntax

Design time: \<PARAM NAME="URL" VALUE="Server"\>

Run time: DataControl.URL="Server"

## Parameters

  - *Server*

  - A **String** value that contains a valid URL.

  - *DataControl*

  - An object variable that represents a **DataControl** object.

## Remarks

Typically, the URL identifies an Active Server Page (.asp) file that can produce and return a [Recordset](recordset-object-ado.md). Therefore, the user can obtain a **Recordset** without having to invoke the server-side [DataFactory](datafactory-object-rdsserver.md) object, or program a custom business object.

If the **URL** property has been set, [SubmitChanges](submitchanges-method-rds.md) will submit changes to the location specified by the URL.

