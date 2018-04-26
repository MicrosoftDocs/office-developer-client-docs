---
title: "Recordset2.UpdateOptions Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 2692480e-c472-dd8e-f91a-939776822ece

---

# Recordset2.UpdateOptions Property (DAO)

## Syntax

 *expression*  . **UpdateOptions**
  
 *expression*  A variable that represents a **Recordset2** object. 
  
## Remarks

When a batch-mode **[Update](recordset2-update-method-dao.md)** is executed, DAO and the client batch cursor library create a series of SQL UPDATE statements to make the needed changes. An SQL WHERE clause is created for each update to isolate the records that are marked as changed by the **[RecordStatus](recordset2-recordstatus-property-dao.md)** property. Because some remote servers use triggers or other ways to enforce referential integrity, is it often important to limit the fields being updated to just those affected by the change. To do this, set the **UpdateOptions** property to one of the constants **dbCriteriaKey**, **dbCriteriaModValues**, **dbCriteriaAllCols**, or **dbCriteriaTimeStamp**. This way, only the absolute minimum amount of trigger code is executed. As a result, the update operation is executed more quickly, and with fewer potential errors. 
  
You can also concatenate either of the constants **dbCriteriaDeleteInsert** or **dbCriteriaUpdate** to determine whether to use a set of SQL DELETE and INSERT statements or an SQL UPDATE statement for each update when sending batched modifications back to the server. In the former case, two separate operations are required to update the record. In some cases, especially where the remote system implements DELETE, INSERT, and UPDATE triggers, choosing the correct **UpdateOptions** property setting can significantly impact performance. 
  
If you don't specify any constants, **dbCriteriaUpdate** and **dbCriteriaKey** will be used. 
  
Newly added records will always generate INSERT statements and deleted records will always generate DELETE statements, so this property only applies to how the cursor library updates modified records.
  

