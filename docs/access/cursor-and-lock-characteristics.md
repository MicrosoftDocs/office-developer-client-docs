---
title: "Cursor and Lock Characteristics"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 5f8b6700-14f6-d342-42f6-cc8e89c71a1a
description: "While the characteristics of a cursor depend upon capabilities of the provider, the following advantages and disadvantages generally apply to the various types of cursors and locks."
---

# Cursor and Lock Characteristics

While the characteristics of a cursor depend upon capabilities of the provider, the following advantages and disadvantages generally apply to the various types of cursors and locks.
  
|**Cursor or lock type**|**Advantages**|**Disadvantages**|
|:-----|:-----|:-----|
|**adOpenForwardOnly** <br/> | Low resource requirements  <br/> | Cannot scroll backward  <br/>  No data concurrency  <br/> |
|**adOpenStatic** <br/> | Scrollable  <br/> | No data concurrency  <br/> |
|**adOpenKeyset** <br/> | Some data concurrency  <br/>  Scrollable  <br/> | Higher resource requirements  <br/>  Not available in disconnected scenario  <br/> |
|**adOpenDynamic** <br/> | High data concurrency  <br/>  Scrollable  <br/> | Highest resource requirements  <br/>  Not available in disconnected scenario  <br/> |
|**adLockReadOnly** <br/> | Low resource requirements  <br/>  Highly scalable  <br/> | Data not updatable through cursor  <br/> |
|**adLockBatchOptimistic** <br/> | Batch updates  <br/>  Allows disconnected scenarios  <br/>  Other users able to access data  <br/> | Data can be changed by multiple users at once  <br/> |
|**adLockPessimistic** <br/> | Data cannot be changed by other users while locked  <br/> | Prevents other users from accessing data while locked  <br/> |
|**adLockOptimistic** <br/> | Other users able to access data  <br/> | Data can be changed by multiple users at once  <br/> |
   

