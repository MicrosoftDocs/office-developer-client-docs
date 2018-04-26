---
title: "Recordset.MovePrevious Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052872
  
localization_priority: Normal
ms.assetid: 82a3bc3e-5221-9a1a-1350-47bc6759edeb
description: "Moves to the previous record in a specified Recordset object and make that record the current record."
---

# Recordset.MovePrevious Method (DAO)

Moves to the previous record in a specified **Recordset** object and make that record the current record. 
  
## Syntax

 *expression*  . **MovePrevious**
  
 *expression*  A variable that represents a **Recordset** object. 
  
## Remarks

Use the **Move** methods to move from record to record without applying a condition. 
  
If you edit the current record, be sure you use the **Update** method to save the changes before you move to another record. If you move to another record without updating, your changes are lost without warning. 
  
When you open a **Recordset**, the first record is current and the **BOF** property is **False**. If the **Recordset** contains no records, the **BOF** property is **True**, and there is no current record. 
  
If you use **MovePrevious** when the first record is current, the **BOF** property is **True**, and there is no current record. If you use **MovePrevious** again, an error occurs, and **BOF** remains **True**. 
  
If  _recordset_ refers to a table-type **Recordset** (Microsoft Access workspaces only), movement follows the current index. You can set the current index by using the **Index** property. If you don't set the current index, the order of returned records is undefined. 
  
You can't use the **MoveFirst**, **MoveLast**, and **MovePrevious** methods on a forward-only-type **Recordset** object. 
  
To move the position of the current record in a **Recordset** object a specific number of records forward or backward, use the **Move** method. 
  

