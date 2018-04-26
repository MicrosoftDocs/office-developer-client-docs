---
title: "MaxRecords Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 424b2d41-073a-3fbe-30aa-99fac94f9a81

---

# MaxRecords Property (ADO)

Indicates the maximum number of records to return to a [Recordset](recordset-object-ado.md) from a query. 
  
## Settings and Return Values

Sets or returns a **Long** value that indicates the maximum number of records to return. Default is zero (no limit). 
  
## Remarks

Use the **MaxRecords** property to limit the number of records that the provider returns from the data source. The default setting of this property is zero, which means the provider returns all requested records. 
  
The **MaxRecords** property is read/write when the **Recordset** is closed and read-only when it is open. 
  

