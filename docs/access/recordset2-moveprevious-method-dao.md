---
title: "Recordset2.MovePrevious Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 8c433810-4b19-e7c1-3cee-a0bc50b23e8a
description: "Moves to the previous record in a specified Recordset object and make that record the current record."
---

# Recordset2.MovePrevious Method (DAO)

Moves to the previous record in a specified **Recordset** object and make that record the current record. 
  
## Syntax

 *expression*  . **MovePrevious**
  
 *expression*  A variable that represents a **Recordset2** object. 
  
## Remarks

Use the **Move** methods to move from record to record without applying a condition. 
  
If you edit the current record, be sure you use the **Update** method to save the changes before you move to another record. If you move to another record without updating, your changes are lost without warning. 
  
When you open a **Recordset**, the first record is current and the **BOF** property is **False**. If the **Recordset** contains no records, the **BOF** property is **True**, and there is no current record. 
  
If you use **MovePrevious** when the first record is current, the **BOF** property is **True**, and there is no current record. If you use **MovePrevious** again, an error occurs, and **BOF** remains **True**. 
  
If  _recordset_ refers to a table-type **Recordset** (Microsoft Access workspaces only), movement follows the current index. You can set the current index by using the **Index** property. If you don't set the current index, the order of returned records is undefined. 
  
You can't use the **MoveFirst**, **MoveLast**, and **MovePrevious** methods on a forward-only-type **Recordset** object. 
  
To move the position of the current record in a **Recordset** object a specific number of records forward or backward, use the **Move** method. 
  

