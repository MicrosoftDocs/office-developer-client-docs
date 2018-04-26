---
title: "FetchProgress Event (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 09145d9a-ea5e-b41c-6c54-33ec83e642a9

---

# FetchProgress Event (ADO)

The **FetchProgress** event is called periodically during a lengthy asynchronous operation to report how many more rows have currently been retrieved into the [Recordset](recordset-object-ado.md).
  
## Syntax

 **FetchProgress** *Progress*  ,  *MaxProgress*  ,  *adStatus*  ,  *pRecordset* 
  
## Parameters

-  *Progress* 
    
- A **Long** value indicating the number of records that have currently been retrieved by the fetch operation. 
    
-  *MaxProgress* 
    
- A **Long** value indicating the maximum number of records expected to be retrieved. 
    
-  *adStatus* 
    
- An [EventStatusEnum](eventstatusenum.md) status value. 
    
-  *pRecordset* 
    
- A **Recordset** object that is the object for which the records are being retrieved. 
    
## Remarks

When using **FetchProgress** with a child **Recordset**, be aware that the  *Progress*  and  *MaxProgress*  parameter values are derived from the underlying [Cursor Service](microsoft-cursor-service-for-ole-db-ado-service-component.md) rowset. The values returned represent the total number of records in the underlying rowset, not just the number of records in the current chapter. 
  
> [!NOTE]
> To use **FetchProgress** with Microsoft Visual Basic, Visual Basic 6.0 or later is required. 
  

