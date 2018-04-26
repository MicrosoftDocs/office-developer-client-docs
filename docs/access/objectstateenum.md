---
title: "ObjectStateEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 129d589a-2955-3da9-e60a-7fbfdd6bfbdc

---

# ObjectStateEnum

Specifies whether an object is open or closed, connecting to a data source, executing a command, or retrieving data.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adStateClosed** <br/> |0  <br/> |Indicates that the object is closed.  <br/> |
|**adStateOpen** <br/> |1  <br/> |Indicates that the object is open.  <br/> |
|**adStateConnecting** <br/> |2  <br/> |Indicates that the object is connecting.  <br/> |
|**adStateExecuting** <br/> |4  <br/> |Indicates that the object is executing a command.  <br/> |
|**adStateFetching** <br/> |8  <br/> |Indicates that the rows of the object are being retrieved.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.ObjectState.CLOSED  <br/> |
|AdoEnums.ObjectState.OPEN  <br/> |
|AdoEnums.ObjectState.CONNECTING  <br/> |
|AdoEnums.ObjectState.EXECUTING  <br/> |
|AdoEnums.ObjectState.FETCHING  <br/> |
   

