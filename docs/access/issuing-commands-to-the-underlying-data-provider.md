---
title: "Issuing Commands to the Underlying Data Provider"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 9d8ef3f3-d93c-af67-3114-d2c36c78a802
description: "Any command that does not begin with SHAPE is passed through to the data provider. This is equivalent to issuing a shape command in the formSHAPE {provider command}. These commands do not have to produce a Recordset . For instance,SHAPE {DROP TABLE MyTable} is a perfectly valid shape command, assuming the data provider supports DROP TABLE."
---

# Issuing Commands to the Underlying Data Provider

Any command that does not begin with SHAPE is passed through to the data provider. This is equivalent to issuing a shape command in the form "SHAPE {provider command}". These commands do  *not*  have to produce a **Recordset**. For instance, "SHAPE {DROP TABLE MyTable} is a perfectly valid shape command, assuming the data provider supports DROP TABLE. 
  
This capability allows both normal provider commands and shape commands to share the same connection and transaction.
  

