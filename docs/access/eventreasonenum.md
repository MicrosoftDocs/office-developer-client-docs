---
title: "EventReasonEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 0639928e-d0ef-3db3-887e-f3da03913bc7

---

# EventReasonEnum

Specifies the reason that caused an event to occur.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adRsnAddNew** <br/> |1  <br/> |An operation added a new record.  <br/> |
|**adRsnClose** <br/> |9  <br/> |An operation closed the **Recordset**.  <br/> |
|**adRsnDelete** <br/> |2  <br/> |An operation deleted a record.  <br/> |
|**adRsnFirstChange** <br/> |11  <br/> |An operation made the first change to a record.  <br/> |
|**adRsnMove** <br/> |10  <br/> |An operation moved the record pointer within the **Recordset**.  <br/> |
|**adRsnMoveFirst** <br/> |12  <br/> |An operation moved the record pointer to the first record in the **Recordset**.  <br/> |
|**adRsnMoveLast** <br/> |15  <br/> |An operation moved the record pointer to the last record in the **Recordset**.  <br/> |
|**adRsnMoveNext** <br/> |13  <br/> |An operation moved the record pointer to the next record in the **Recordset**.  <br/> |
|**adRsnMovePrevious** <br/> |14  <br/> |An operation moved the record pointer to the previous record in the **Recordset**.  <br/> |
|**adRsnRequery** <br/> |7  <br/> |An operation requeried the [Recordset](recordset-object-ado.md).  <br/> |
|**adRsnResynch** <br/> |8  <br/> |An operation resynchronized the **Recordset** with the database.  <br/> |
|**adRsnUndoAddNew** <br/> |5  <br/> |An operation reversed the addition of a new record.  <br/> |
|**adRsnUndoDelete** <br/> |6  <br/> |An operation reversed the deletion of a record.  <br/> |
|**adRsnUndoUpdate** <br/> |4  <br/> |An operation reversed the update of a record.  <br/> |
|**adRsnUpdate** <br/> |3  <br/> |An operation updated an existing record.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.EventReason.ADDNEW  <br/> |
|AdoEnums.EventReason.CLOSE  <br/> |
|AdoEnums.EventReason.DELETE  <br/> |
|AdoEnums.EventReason.FIRSTCHANGE  <br/> |
|AdoEnums.EventReason.MOVE  <br/> |
|AdoEnums.EventReason.MOVEFIRST  <br/> |
|AdoEnums.EventReason.MOVELAST  <br/> |
|AdoEnums.EventReason.MOVENEXT  <br/> |
|AdoEnums.EventReason.MOVEPREVIOUS  <br/> |
|AdoEnums.EventReason.REQUERY  <br/> |
|AdoEnums.EventReason.RESYNCH  <br/> |
|AdoEnums.EventReason.UNDOADDNEW  <br/> |
|AdoEnums.EventReason.UNDODELETE  <br/> |
|AdoEnums.EventReason.UNDOUPDATE  <br/> |
|AdoEnums.EventReason.UPDATE  <br/> |
   

