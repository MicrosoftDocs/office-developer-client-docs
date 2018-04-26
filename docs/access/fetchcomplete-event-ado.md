---
title: "FetchComplete Event (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 4863d5b5-7d77-bdef-c511-f85c9e6dec9d

---

# FetchComplete Event (ADO)

The **FetchComplete** event is called after all the records in a lengthy asynchronous operation have been retrieved into the [Recordset](recordset-object-ado.md).
  
## Syntax

 **FetchComplete** *pError*  ,  *adStatus*  ,  *pRecordset* 
  
## Parameters

-  *pError* 
    
- An [Error](error-object-ado.md) object. It describes the error that occurred if the value of **adStatus** is **adStatusErrorsOccurred**; otherwise it is not set. 
    
-  *adStatus* 
    
- [EventStatusEnum](eventstatusenum.md)
    
    Before this event returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications. 
    
-  *pRecordset* 
    
- A **Recordset** object. The object for which the records were retrieved. 
    
## Remarks

To use **FetchComplete** with Microsoft Visual Basic, Visual Basic 6.0 or later is required. 
  

