---
title: "ExecuteOptions Property (RDS)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: fb244cbd-9a03-9128-1373-694c9061c9da

---

# ExecuteOptions Property (RDS)

Indicates whether asynchronous execution is enabled.
  
## Settings and Return Values

Sets or returns one of the following values.
  
|**Constant**|**Description**|
|:-----|:-----|
|**adcExecSync** <br/> |Executes the next refresh of the [Recordset](recordset-object-ado.md) synchronously.  <br/> |
|**adcExecAsync** <br/> |Default. Executes the next refresh of the **Recordset** asynchronously.  <br/> |
   
> [!NOTE]
> Each client-side executable file that uses these constants must provide declarations for them. You can cut and paste the constant declarations that you want from the file Adcvbs.inc, located in the C:\Program Files\Common Files\System\MSADC folder. 
  
## Remarks

If **ExecuteOptions** is set to **adcExecAsync**, then this asynchronously executes the next **Refresh** call on the [RDS.DataControl](datacontrol-object-rds.md) object's **Recordset**. 
  
If you try to call [Reset](reset-method-rds.md), [Refresh](refresh-method-rds.md), [SubmitChanges](submitchanges-method-rds.md), [CancelUpdate](cancelupdate-method-ado.md), or [Recordset](recordset-sourcerecordset-properties-rds.md) while another asynchronous operation that might change the [RDS.DataControl](datacontrol-object-rds.md) object's **Recordset** is executing, an error occurs. 
  
If an error occurs during an asynchronous operation, the **RDS.DataControl** object's [ReadyState](readystate-property-rds.md) value changes from **adcReadyStateLoaded** to **adcReadyStateComplete**, and the **Recordset** property value remains  *Nothing*  . 
  

