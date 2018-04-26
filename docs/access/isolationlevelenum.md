---
title: "IsolationLevelEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 438af3f3-65ed-237d-94d8-f3aff6addd3b

---

# IsolationLevelEnum

Specifies the level of transaction isolation for a [Connection](connection-object-ado.md) object. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adXactUnspecified** <br/> |-1  <br/> |Indicates that the provider is using a different isolation level than specified, but that the level cannot be determined.  <br/> |
|**adXactChaos** <br/> |16  <br/> |Indicates that pending changes from more highly isolated transactions cannot be overwritten.  <br/> |
|**adXactBrowse** <br/> |256  <br/> |Indicates that from one transaction you can view uncommitted changes in other transactions.  <br/> |
|**adXactReadUncommitted** <br/> |256  <br/> |Same as **adXactBrowse**.  <br/> |
|**adXactCursorStability** <br/> |4096  <br/> |Indicates that from one transaction you can view changes in other transactions only after they have been committed.  <br/> |
|**adXactReadCommitted** <br/> |4096  <br/> |Same as **adXactCursorStability**.  <br/> |
|**adXactRepeatableRead** <br/> |65536  <br/> |Indicates that from one transaction you cannot see changes made in other transactions, but that requerying can retrieve new **Recordset** objects.  <br/> |
|**adXactIsolated** <br/> |1048576  <br/> |Indicates that transactions are conducted in isolation of other transactions.  <br/> |
|**adXactSerializable** <br/> |1048576  <br/> |Same as **adXactIsolated**.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.IsolationLevel.UNSPECIFIED  <br/> |
|AdoEnums.IsolationLevel.CHAOS  <br/> |
|AdoEnums.IsolationLevel.BROWSE  <br/> |
|AdoEnums.IsolationLevel.READUNCOMMITTED  <br/> |
|AdoEnums.IsolationLevel.CURSORSTABILITY  <br/> |
|AdoEnums.IsolationLevel.READCOMMITTED  <br/> |
|AdoEnums.IsolationLevel.REPEATABLEREAD  <br/> |
|AdoEnums.IsolationLevel.ISOLATED  <br/> |
|AdoEnums.IsolationLevel.SERIALIZABLE  <br/> |
   

