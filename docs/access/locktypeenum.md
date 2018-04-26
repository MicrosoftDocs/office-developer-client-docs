---
title: "LockTypeEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 966b4952-5591-4a99-82d5-99cb9ae3fc72

---

# LockTypeEnum

Specifies the type of lock placed on records during editing.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adLockBatchOptimistic** <br/> |4  <br/> |Indicates optimistic batch updates. Required for batch update mode.  <br/> |
|**adLockOptimistic** <br/> |3  <br/> |Indicates optimistic locking, record by record. The provider uses optimistic locking, locking records only when you call the [Update](update-method-ado.md) method.  <br/> |
|**adLockPessimistic** <br/> |2  <br/> |Indicates pessimistic locking, record by record. The provider does what is necessary to ensure successful editing of the records, usually by locking records at the data source immediately after editing.  <br/> |
|**adLockReadOnly** <br/> |1  <br/> |Indicates read-only records. You cannot alter the data.  <br/> |
|**adLockUnspecified** <br/> |-1  <br/> |Does not specify a type of lock. For clones, the clone is created with the same lock type as the original.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.LockType.BATCHOPTIMISTIC  <br/> |
|AdoEnums.LockType.OPTIMISTIC  <br/> |
|AdoEnums.LockType.PESSIMISTIC  <br/> |
|AdoEnums.LockType.READONLY  <br/> |
|AdoEnums.LockType.UNSPECIFIED  <br/> |
   

