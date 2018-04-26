---
title: "WillExecute Event (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 9f516bfd-246d-9817-4ca3-64598ab466f7

---

# WillExecute Event (ADO)

The **WillExecute** event is called just before a pending command executes on a connection. 
  
## Syntax

 **WillExecute** *Source*  ,  *CursorType*  ,  *LockType*  ,  *Options*  ,  *adStatus*  ,  *pCommand*  ,  *pRecordset*  ,  *pConnection* 
  
## Parameters

-  *Source* 
    
- A **String** that contains an SQL command or a stored procedure name. 
    
-  *CursorType* 
    
- A [CursorTypeEnum](cursortypeenum.md) that contains the type of cursor for the **Recordset** that will be opened. With this parameter, you can change the cursor to any type during a **Recordset**[Open](open-method-ado-recordset.md) operation.  *CursorType*  will be ignored for any other operation. 
    
-  *LockType* 
    
- A [LockTypeEnum](locktypeenum.md) that contains the lock type for the **Recordset** that will be opened. With this parameter, you can change the lock to any type during a **Recordset** **Open** operation.  *LockType*  will be ignored for any other operation. 
    
-  *Options* 
    
- A **Long** value that indicates options that can be used to execute the command or open the **Recordset**. 
    
-  *adStatus* 
    
- [EventStatusEnum](eventstatusenum.md)
    
    Before this event returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications, or **adStatusCancel** to request cancellation of the operation that caused this event. 
    
-  *pCommand* 
    
- The [Command](command-object-ado.md) object for which this event notification applies. 
    
-  *pRecordset* 
    
- The [Recordset](recordset-object-ado.md) object for which this event notification applies. 
    
-  *pConnection* 
    
- The [Connection](connection-object-ado.md) object for which this event notification applies. 
    
## Remarks

A **WillExecute** event may occur due to a **Connection.**[Execute](http://msdn.microsoft.com/library/af190bd9-7167-df59-29ca-a9a86c4957fd%28Office.15%29.aspx), **Command.**[Execute](http://msdn.microsoft.com/library/01812c8c-403e-4428-23f6-86bda747bd0e%28Office.15%29.aspx), or **Recordset.**[Open](open-method-ado-recordset.md) method The  *pConnection*  parameter should always contain a valid reference to a **Connection** object. If the event is due to **Connection.Execute**, the  *pRecordset*  and  *pCommand*  parameters are set to **Nothing**. If the event is due to **Recordset.Open**, the  *pRecordset*  parameter will reference the **Recordset** object and the  *pCommand*  parameter is set to **Nothing**. If the event is due to **Command.Execute**, the  *pCommand*  parameter will reference the **Command** object and the  *pRecordset*  parameter is set to **Nothing**. 
  
 **WillExecute** allows you to examine and modify the pending execution parameters. This event may return a request that the pending command be canceled. 
  

