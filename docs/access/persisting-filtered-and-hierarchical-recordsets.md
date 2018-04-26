---
title: "Persisting Filtered and Hierarchical Recordsets"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 3648a997-dac7-d8a3-3cca-a6827f26a4f0
description: "If the Filter property is in effect for the Recordset , only the rows accessible under the filter are saved. If the Recordset is hierarchical, the current child Recordset and its children are saved, including the parent Recordset . If the Save method of a child Recordset is called, the child and all its children are saved, but the parent is not. For more information about hierarchical Recordsets , see Chapter 9: Data Shaping."
---

# Persisting Filtered and Hierarchical Recordsets

If the [Filter](filter-property-ado.md) property is in effect for the **Recordset**, only the rows accessible under the filter are saved. If the **Recordset** is hierarchical, the current child **Recordset** and its children are saved, including the parent **Recordset**. If the **Save** method of a child **Recordset** is called, the child and all its children are saved, but the parent is not. For more information about hierarchical **Recordsets**, see [Chapter 9: Data Shaping](chapter-9-data-shaping.md).
  
> [!NOTE]
> Some limitations apply when saving hierarchical **Recordsets** (data shapes) in XML format. For more information, see [Hierarchical Recordsets in XML](hierarchical-recordsets-in-xml.md). 
  

