---
title: "Recordset2.MoveLast Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 32717786-c59c-ec22-666b-fc78e4265c5a
description: "Moves to the last record in a specified Recordset object and make that record the current record."
---

# Recordset2.MoveLast Method (DAO)

Moves to the last record in a specified **Recordset** object and make that record the current record. 
  
## Syntax

 *expression*  . **MoveLast**( ** *Options* ** ) 
  
 *expression*  A variable that represents a **Recordset2** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Options_ <br/> |Optional  <br/> |**Long** <br/> |Set to **dbRunAsync** to rune the call to **MoveLast** asynchronously.  <br/> |
   
## Remarks

Use the **Move** methods to move from record to record without applying a condition. 
  
If you edit the current record, be sure you use the **Update** method to save the changes before you move to another record. If you move to another record without updating, your changes are lost without warning. 
  
When you open a **Recordset**, the first record is current and the **BOF** property is **False**. If the **Recordset** contains no records, the **BOF** property is **True**, and there is no current record. 
  
If the first or last record is already current when you use **MoveFirst** or **MoveLast**, the current record doesn't change. 
  
If  _recordset_ refers to a table-type **Recordset** (Microsoft Access workspaces only), movement follows the current index. You can set the current index by using the **Index** property. If you don't set the current index, the order of returned records is undefined. 
  
> [!NOTE]
> You can use the **MoveLast** method to fully populate a dynaset- or snapshot-type **Recordset** to provide the current number of records in the **Recordset**. However, if you use **MoveLast** in this way, you can slow down your application's performance. You should only use **MoveLast** to get a record count if it is absolutely necessary to obtain an accurate record count on a newly opened **Recordset**. If you use the **dbRunAsync** constant with **MoveLast**, the method call is asynchronous. You can use the **StillExecuting** property to determine when the **Recordset** is fully populated, and you can use the **Cancel** method to terminate execution of the asynchronous **MoveLast** method call. 
  
You can't use the **MoveFirst**, **MoveLast**, and **MovePrevious** methods on a forward-only-type **Recordset** object. 
  
To move the position of the current record in a **Recordset** object a specific number of records forward or backward, use the **Move** method. 
  

