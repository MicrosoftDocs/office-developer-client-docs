---
title: "Batch Mode"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: b73921f6-5a12-9b26-ea65-99b32dd763f6
description: "Batch mode is in effect when the LockType property is set to adLockBatchOptimistic and batch updating is supported by the provider. Certain lock type settings are not available depending on cursor location. For instance, a pessimistic lock type is not available when the CursorLocation is set to adUseClient . Conversely, a provider may not support a batch optimistic lock when the cursor location is on the server. You should use batch updating with either a keyset or static cursor only."
---

# Batch Mode

Batch mode is in effect when the **LockType** property is set to **adLockBatchOptimistic** and batch updating is supported by the provider. Certain lock type settings are not available depending on cursor location. For instance, a pessimistic lock type is not available when the **CursorLocation** is set to **adUseClient**. Conversely, a provider may not support a batch optimistic lock when the cursor location is on the server. You should use batch updating with either a keyset or static cursor only. 
  
The **UpdateBatch** method is used to send **Recordset** changes held in the copy buffer to the server to update the data source. In the following section, we will open a **Recordset** in batch mode, make changes to the copy buffer, and then send our changes to the data source using a call to **UpdateBatch**. 
  

