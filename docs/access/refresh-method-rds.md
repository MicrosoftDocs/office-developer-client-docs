---
title: "Refresh Method (RDS)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 968baa7c-9128-7155-a1eb-d77aedda6601

---

# Refresh Method (RDS)

Requeries the data source specified in the [Connect](connect-property-rds.md) property and updates the query results. 
  
## Syntax

 *DataControl*  . **Refresh**
  
## Parameters

-  *DataControl* 
    
- An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object. 
    
## Remarks

You must set the [Connect](connect-property-rds.md), [Server](server-property-rds.md), and [SQL](http://msdn.microsoft.com/library/210adcbb-5c89-150b-4c61-6a52dea9af56%28Office.15%29.aspx) properties before you use the **Refresh** method. All data-bound controls on the form associated with an **RDS.DataControl** object will reflect the new set of records. Any pre-existing [Recordset](recordset-object-ado.md) object is released, and any unsaved changes are discarded. The **Refresh** method automatically makes the first record the current record. 
  
It's a good idea to call the **Refresh** method periodically when you work with data. If you retrieve data, and then leave it on your client machine for a while, it is likely to become out of date. It's possible that any changes you make will fail, because someone else might have changed the record and submitted changes before you. 
  

