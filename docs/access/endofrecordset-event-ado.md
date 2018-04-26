---
title: "EndOfRecordset Event (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 8995b851-dff6-2525-1d62-a2cfb4f95393
---

# EndOfRecordset Event (ADO)

The **EndOfRecordset** event is called when there is an attempt to move to a row past the end of the [Recordset](recordset-object-ado.md).
  
## Syntax

 **EndOfRecordset** *fMoreData*  ,  *adStatus*  ,  *pRecordset* 
  
## Parameters

-  *fMoreData* 
    
- A **VARIANT_BOOL** value that, if set to VARIANT_TRUE, indicates more rows have been added to the **Recordset**. 
    
-  *adStatus* 
    
- [EventStatusEnum](eventstatusenum.md)
    
    When **EndOfRecordset** is called, this parameter is set to **adStatusOK** if the operation that caused the event was successful. It is set to **adStatusCantDeny** if this event cannot request cancellation of the operation that caused this event. 
    
    Before **EndOfRecordset** returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications. 
    
-  *pRecordset* 
    
- A **Recordset** object. The **Recordset** for which this event occurred. 
    
## Remarks

An **EndOfRecordset** event may occur if the [MoveNext](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) operation fails. 
  
This event handler is called when an attempt is made to move past the end of the **Recordset** object, perhaps as a result of calling **MoveNext**. However, while in this event, you could retrieve more records from a database and append them to the end of the **Recordset**. In that case, set  *fMoreData*  to VARIANT_TRUE, and return from **EndOfRecordset**. Then call **MoveNext** again to access the newly retrieved records. 
  

