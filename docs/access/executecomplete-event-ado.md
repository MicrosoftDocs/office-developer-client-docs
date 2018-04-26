---
title: "ExecuteComplete Event (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 47317d97-e373-32f4-9438-2dff46b8d367

---

# ExecuteComplete Event (ADO)

The **ExecuteComplete** event is called after a command has finished executing. 
  
## Syntax

 **ExecuteComplete** *RecordsAffected*  ,  *pError*  ,  *adStatus*  ,  *pCommand*  ,  *pRecordset*  ,  *pConnection* 
  
## Parameters

-  *RecordsAffected* 
    
- A **Long** value indicating the number of records affected by the command. 
    
-  *pError* 
    
- An [Error](error-object-ado.md) object. It describes the error that occurred if the value of **adStatus** is **adStatusErrorsOccurred**; otherwise it is not set. 
    
-  *adStatus* 
    
- [EventStatusEnum](eventstatusenum.md)
    
    Before this event returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications. 
    
-  *pCommand* 
    
- The [Command](command-object-ado.md) object that was executed. Contains a **Command** object even when calling **Connection.Execute** or **Recordset.Open** without explicitly creating a **Command**, in which cases the **Command** object is created internally by ADO. 
    
-  *pRecordset* 
    
- A [Recordset](recordset-object-ado.md) object that is the result of the executed command. This **Recordset** may be empty. You should never destroy this Recordset object from within this event handler. Doing so will result in an Access Violation when ADO tries to access an object that no longer exists. 
    
-  *pConnection* 
    
- A [Connection](connection-object-ado.md) object. The connection over which the operation was executed. 
    
## Remarks

An **ExecuteComplete** event may occur due to the **Connection.**[Execute](http://msdn.microsoft.com/library/af190bd9-7167-df59-29ca-a9a86c4957fd%28Office.15%29.aspx), **Command.**[Execute](http://msdn.microsoft.com/library/01812c8c-403e-4428-23f6-86bda747bd0e%28Office.15%29.aspx), **Recordset.**[Open](open-method-ado-recordset.md), **Recordset.**[Requery](requery-method-ado.md), or **Recordset.**[NextRecordset](nextrecordset-method-ado.md) methods. 
  

