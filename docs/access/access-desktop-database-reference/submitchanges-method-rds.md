---
title: SubmitChanges Method (RDS)
TOCTitle: SubmitChanges Method (RDS)
ms:assetid: ecaea12d-7e1a-095d-17e7-d631ef230b90
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250201(v=office.15)
ms:contentKeyID: 48548521
ms.date: 09/18/2015
mtps_version: v=office.15
---

# SubmitChanges Method (RDS)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Parameters  
Remarks  

Submits pending changes of the locally cached and updatable [Recordset](recordset-object-ado.md) to the data source specified in the [Connect](connect-property-rds.md) property or the [URL](url-property-rds.md) property.

## Syntax

*DataControl*.SubmitChanges

*DataFactory*.SubmitChanges*Connection*, *Recordset*

## Parameters

  - *DataControl*

  - An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object.

  - *DataFactory*

  - An object variable that represents an [RDSServer.DataFactory](datafactory-object-rdsserver.md) object.

  - *Connection*

  - A **String** value that represents the connection created with the **RDS.DataControl** object's **Connect** property.

  - *Recordset*

  - An object variable that represents a **Recordset** object.

## Remarks

The [Connect](connect-property-rds.md), [Server](server-property-rds.md), and [SQL](https://msdn.microsoft.com/en-us/library/jj248989\(v=office.15\)) properties must be set before you can use the **SubmitChanges** method with the **RDS.DataControl** object.

If you call the [CancelUpdate](cancelupdate-method-rds.md) method after you have called **SubmitChanges** for the same **Recordset** object, the **CancelUpdate** call fails because the changes have already been committed.

Only the changed records are sent for modification, and either all of the changes succeed or all of them fail together.

You can use **SubmitChanges** only with the *default* **RDSServer.DataFactory** object. Custom business objects can't use this method.

If the **URL** property has been set, **SubmitChanges** will submit changes to the location specified by the URL.

