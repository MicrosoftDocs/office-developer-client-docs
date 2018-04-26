---
title: "Reshaping"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 89c6a0d6-3bf4-36ae-26ec-d4e60f920490
description: "A Recordset created by a clause of a shape command may be assigned an alias name (typically with the AS keyword). The alias of a shaped Recordset can be referenced in an entirely different command. That is, you may reuse, or reshape , a previously shaped Recordset in a new shape command. To support this feature, ADO provides a property, Reshape Name."
---

# Reshaping

A **Recordset** created by a clause of a shape command may be assigned an  *alias*  name (typically with the AS keyword). The alias of a shaped **Recordset** can be referenced in an entirely different command. That is, you may reuse, or  *reshape*  , a previously shaped **Recordset** in a new shape command. To support this feature, ADO provides a property, [Reshape Name](reshape-name-property-dynamic-ado.md).
  
Reshaping has two main functions. The first is to associate an existing **Recordset** with a new parent **Recordset**. 
  
## Example

```
 
. . . 
rs1.Open "SHAPE {select * from Customers} " &amp; _ 
 "APPEND ({select * from Orders} AS chapOrders " &amp; _ 
 "RELATE CustomerID to CustomerID)", cn 
 
rs2.Open "SHAPE {select * from Employees} " &amp; _ 
 "APPEND (chapOrders RELATE EmployeeID to EmployeeID)", cn 
. . . 

```

The second function is to enable non-chaptered access to existing child **Recordset** objects, using the syntax "SHAPE <recordset reshape name>". 
  
> [!NOTE]
> You cannot append columns to an existing **Recordset**, reshape a parameterized **Recordset** or the **Recordset** objects in any intervening COMPUTE clause, or perform aggregate operations on any **Recordset** descendant from the **Recordset** being reshaped. The **Recordset** being reshaped and the new shape command must both use the same [Connection](connection-object-ado.md). 
  

