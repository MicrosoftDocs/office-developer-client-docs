---
title: "StayInSync Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 02c95c10-4032-14e1-e506-f334a8787142

---

# StayInSync Property (ADO)

Indicates, in a hierarchical [Recordset](recordset-object-ado.md) object, whether the reference to the underlying child records (that is, the  *chapter*  ) changes when the parent row position changes. 
  
## Settings and Return Values

Sets or returns a **Boolean** value. The default value is **True**. If **True**, the chapter will be updated if the parent **Recordset** object changes row position; if **False**, the chapter will continue to refer to data in the previous chapter even though the parent **Recordset** object has changed row position. 
  
## Remarks

This property applies to hierarchical Recordsets, such as those supported by the [Microsoft Data Shaping Service for OLE DB](microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), and must be set on the parent **Recordset** before the child **Recordset** is retrieved. This property simplifies navigating hierarchical recordsets. 
  

