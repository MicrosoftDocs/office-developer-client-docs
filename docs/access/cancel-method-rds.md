---
title: "Cancel Method (RDS)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 08f667c2-7a3f-c2e7-7bdf-3eb533defa33
---

# Cancel Method (RDS)

Cancels execution of a pending, asynchronous method call.
  
## Syntax

 *RDS*  .  *DataControl*  . **Cancel**
  
## Remarks

When you call **Cancel**, [ReadyState](readystate-property-rds.md) is automatically set to **adcReadyStateLoaded**, and the [Recordset](recordset-object-ado.md) will be empty. 
  

