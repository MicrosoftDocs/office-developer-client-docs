---
title: "ReadyState Property (RDS)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e7b62205-a604-ef43-2f5d-9b51b46d2b5a

---

# ReadyState Property (RDS)

Indicates the progress of a [DataControl](datacontrol-object-rds.md) object as it retrieves data into its [Recordset](recordset-object-ado.md) object. 
  
## Settings and Return Values

Sets or returns one of the following values.
  
|**Value**|**Description**|
|:-----|:-----|
|**adcReadyStateLoaded** <br/> |The current query is still executing and no rows have been fetched. The **DataControl** object's **Recordset** is not available for use.  <br/> |
|**adcReadyStateInteractive** <br/> |An initial set of rows retrieved by the current query has been stored in the **DataControl** object's **Recordset** and are available for use. The remaining rows are still being fetched.  <br/> |
|**adcReadyStateComplete** <br/> |All rows retrieved by the current query have been stored in the **DataControl** object's **Recordset** and are available for use. This state will also exist if an operation aborted due to an error, or if the **Recordset** object is not initialized.  <br/> |
   
> [!NOTE]
> Each client-side executable file that uses these constants must provide declarations for them. You can cut and paste the constant declarations you want from the file Adcvbs.inc, located in the C:\Program Files\Common Files\System\MSADC folder. 
  
## Remarks

Use the [onReadyStateChange](onreadystatechange-event-rds.md) event to monitor changes in the **ReadyState** property during an asynchronous query operation. This is more efficient than periodically checking the value of the property. 
  
If an error occurs during an asynchronous operation, the **ReadyState** property changes to **adcReadyStateComplete**, the [State](state-property-ado.md) property changes from **adStateExecuting** to **adStateClosed**, and the **Recordset** object [Value](value-property-ado.md) property remains  *Nothing*  . 
  

