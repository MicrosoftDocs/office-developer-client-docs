---
title: "FilterGroupEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 141f8f9a-c188-5937-91cc-3155eaebebd2

---

# FilterGroupEnum

Specifies the group of records to be filtered from a [Recordset](recordset-object-ado.md).
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adFilterAffectedRecords** <br/> |2  <br/> |Filters for viewing only records affected by the last [Delete](delete-method-ado-recordset.md), [Resync](resync-method-ado.md), [UpdateBatch](updatebatch-method-ado.md), or [CancelBatch](cancelbatch-method-ado.md) call.  <br/> |
|**adFilterConflictingRecords** <br/> |5  <br/> |Filters for viewing the records that failed the last batch update.  <br/> |
|**adFilterFetchedRecords** <br/> |3  <br/> |Filters for viewing the records in the current cache — that is, the results of the last call to retrieve records from the database.  <br/> |
|**adFilterNone** <br/> |0  <br/> |Removes the current filter and restores all records for viewing.  <br/> |
|**adFilterPendingRecords** <br/> |1  <br/> |Filters for viewing only records that have changed but have not yet been sent to the server. Applicable only for batch update mode.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.FilterGroup.AFFECTEDRECORDS  <br/> |
|AdoEnums.FilterGroup.CONFLICTINGRECORDS  <br/> |
|AdoEnums.FilterGroup.FETCHEDRECORDS  <br/> |
|AdoEnums.FilterGroup.NONE  <br/> |
|AdoEnums.FilterGroup.PENDINGRECORDS  <br/> |
   

