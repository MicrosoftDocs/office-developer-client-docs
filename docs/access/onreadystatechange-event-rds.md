---
title: "onReadyStateChange Event (RDS)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 88102ee5-cca9-8ccb-5aca-55cda71abc4d

---

# onReadyStateChange Event (RDS)

The **onReadyStateChange** event is called whenever the value of the [ReadyState](readystate-property-rds.md) property changes. 
  
## Syntax

 **onReadyStateChange**
  
## Parameters

None.
  
## Remarks

The **ReadyState** property reflects the progress of an [RDS.DataControl](datacontrol-object-rds.md) object as it asynchronously retrieves data into its [Recordset](recordset-object-ado.md) object. Use the **onReadyStateChange** event to monitor changes in the **ReadyState** property whenever they occur. This is more efficient than periodically checking the property's value. 
  

