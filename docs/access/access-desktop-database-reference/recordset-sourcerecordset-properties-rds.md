---
title: Recordset, SourceRecordset Properties (RDS)
TOCTitle: Recordset, SourceRecordset Properties (RDS)
ms:assetid: 5f4bb72d-ddfa-41c0-c353-b3a6632b4a91
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249345(v=office.15)
ms:contentKeyID: 48545160
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset, SourceRecordset Properties (RDS)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameters  
Remarks  

Indicates the **Recordset** object returned from a custom business object.

## Syntax

*DataControl*.SourceRecordset = *Recordset*

*Recordset* = *DataControl*.Recordset

## Parameters

  - *DataControl*

  - An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object.

  - *Recordset*

  - An object variable that represents a **Recordset** object.

## Remarks

You can set the **SourceRecordset** property to a [Recordset](recordset-object-ado.md) returned from a custom business object.

These properties allow an application to handle the binding process by means of a custom process. They receive a rowset wrapped in a **Recordset** so that you can interact directly with the **Recordset**, performing actions such as setting properties or iterating through the **Recordset**.

You can set the **SourceRecordset** property or read the **Recordset** property at run time in scripting code.

**SourceRecordset** is a write-only property, in contrast to the **Recordset** property, which is a read-only property.

