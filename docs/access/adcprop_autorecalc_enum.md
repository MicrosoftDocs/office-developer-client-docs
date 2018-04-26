---
title: "ADCPROP_AUTORECALC_ENUM"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 79ed16c1-964d-bf88-22c9-aa0a51303da6
---

# ADCPROP_AUTORECALC_ENUM

Specifies when the [MSDataShape](microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) provider re-calculates aggregate and calculated columns in a hierarchical Recordset. 
  
These constants are only used with the **MSDataShape** provider and the **Recordset** " **Auto Recalc** " dynamic property, which is referenced in the [ADO Dynamic Property Index](ado-dynamic-property-index.md) and documented in the [Microsoft Cursor Service for OLE DB](microsoft-cursor-service-for-ole-db-ado-service-component.md) or [Microsoft Data Shaping Service for OLE DB](microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) documentation. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adRecalcAlways** <br/> |1  <br/> |Default. Recalculates whenever the **MSDataShape** provider determines values that the calculated columns depend upon have changed.  <br/> |
|**adRecalcUpFront** <br/> |0  <br/> |Calculates only when initially building the hierarchical **Recordset**.  <br/> |
   
 **ADO/WFC Equivalent**
  
These constants do not have ADO/WFC equivalents.
  

