---
title: MoveFirst, MoveLast, MoveNext, and MovePrevious methods (RDS)
TOCTitle: MoveFirst, MoveLast, MoveNext, and MovePrevious methods (RDS)
ms:assetid: 32ef8fa9-c096-b4e7-3396-b88a6a9bd1a2
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249101(v=office.15)
ms:contentKeyID: 48544092
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# MoveFirst, MoveLast, MoveNext, and MovePrevious methods (RDS)

**Applies to**: Access 2013, Office 2013

Moves to the first, last, next, or previous record in a specified [Recordset](recordset-object-ado.md) object.

## Syntax

*DataControl*.Recordset.{ MoveFirst | MoveLast | MoveNext | MovePrevious}

## Parameters

|Parameter|Description|
|:--------|:----------|
|*DataControl* |An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object.|

## Remarks

You can use the **Move** methods with the **RDS.DataControl** object to navigate through the data records in the data-bound controls on a webpage. 

For example, suppose you display a **Recordset** in a grid by binding to an **RDS.DataControl** object. You can then include First, Last, Next, and Previous buttons that users can click to move to the first, last, next, or previous record in the displayed **Recordset**. You do this by calling the **MoveFirst**, **MoveLast**, **MoveNext**, and **MovePrevious** methods of the **RDS.DataControl** object in the onClick procedures for the First, Last, Next, and Previous buttons, respectively. The [Address Book example](address-book-navigation-buttons.md) shows how to do this.

