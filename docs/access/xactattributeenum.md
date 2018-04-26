---
title: "XactAttributeEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 9206698b-7cfa-1229-2701-f2b6949e54fc

---

# XactAttributeEnum

Specifies the transaction attributes of a [Connection](connection-object-ado.md) object. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adXactAbortRetaining** <br/> |262144  <br/> |Performs retaining aborts — that is, calling [RollbackTrans](begintrans-committrans-and-rollbacktrans-methods-ado.md) automatically starts a new transaction. Not all providers support this.  <br/> |
|**adXactCommitRetaining** <br/> |131072  <br/> |Performs retaining commits — that is, calling [CommitTrans](begintrans-committrans-and-rollbacktrans-methods-ado.md) automatically starts a new transaction. Not all providers support this.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.XactAttribute.ABORTRETAINING  <br/> |
|AdoEnums.XactAttribute.COMMITRETAINING  <br/> |
   

