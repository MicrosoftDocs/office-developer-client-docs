---
title: "MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (RDS)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 32ef8fa9-c096-b4e7-3396-b88a6a9bd1a2

---

# MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (RDS)

Moves to the first, last, next, or previous record in a specified [Recordset](recordset-object-ado.md) object. 
  
## Syntax

 *DataControl*  . **Recordset**.{ **MoveFirst** | **MoveLast** | **MoveNext** | **MovePrevious**}
  
## Parameters

-  *DataControl* 
    
- An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object. 
    
## Remarks

You can use the **Move** methods with the **RDS.DataControl** object to navigate through the data records in the data-bound controls on a Web page. For example, suppose you display a **Recordset** in a grid by binding to an **RDS.DataControl** object. You can then include First, Last, Next, and Previous buttons that users can click to move to the first, last, next, or previous record in the displayed **Recordset**. You do this by calling the **MoveFirst**, **MoveLast**, **MoveNext**, and **MovePrevious** methods of the **RDS.DataControl** object in the onClick procedures for the First, Last, Next, and Previous buttons, respectively. The [Address Book example](address-book-navigation-buttons.md) shows how to do this. 
  

