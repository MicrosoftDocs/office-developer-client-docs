---
title: "Recordset Dynamic Properties in XML"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 6ee1f176-9986-4ade-fc97-e3dad8e6bc6b

---

# Recordset Dynamic Properties in XML

## Recordset Dynamic Properties in XML

The following **Recordset** provider-specific properties (from the Client Cursor Engine) are currently persisted into the XML format: 
  
- **Update Resync**
    
- **Unique Table**
    
- **Unique Schema**
    
- **Unique Catalog**
    
- **Resync Command**
    
- **IRowsetChange**
    
- **IRowsetUpdate**
    
- **CommandTimeout**
    
- **BatchSize**
    
- **UpdateCriteria**
    
- **Reshape Name**
    
- **AutoRecalc**
    
These properties are saved in the schema section as attributes of the element definition for the **Recordset** being persisted. These attributes are defined in the rowset schema namespace and must have the prefix "rs:". 
  

