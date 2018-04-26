---
title: "EventStatusEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ae1711bc-2af5-04fd-7d8c-222d8afc9d3d

---

# EventStatusEnum

Specifies the current status of the execution of an event.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adStatusCancel** <br/> |4  <br/> |Requests cancellation of the operation that caused the event to occur.  <br/> |
|**adStatusCantDeny** <br/> |3  <br/> |Indicates that the operation cannot request cancellation of the pending operation.  <br/> |
|**adStatusErrorsOccurred** <br/> |2  <br/> |Indicates that the operation that caused the event failed due to an error or errors.  <br/> |
|**adStatusOK** <br/> |1  <br/> |Indicates that the operation that caused the event was successful.  <br/> |
|**adStatusUnwantedEvent** <br/> |5  <br/> |Prevents subsequent notifications before the event method has finished executing.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.EventStatus.CANCEL  <br/> |
|AdoEnums.EventStatus.CANTDENY  <br/> |
|AdoEnums.EventStatus.ERRORSOCCURRED  <br/> |
|AdoEnums.EventStatus.OK  <br/> |
|AdoEnums.EventStatus.UNWANTEDEVENT  <br/> |
   

