---
title: "The Microsoft Cursor Service for OLE DB"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 31861eef-9860-c884-3c60-9794def7be78
description: "When you select a client-side cursor, or set the CursorLocation property to adUseClient , you are invoking the Microsoft Cursor Service for OLE DB. You might also see references to theClient Cursor Engine, which is essentially the same thing in the context of ADO. This service supplements the cursor-support functions of data providers. As a result, you can perceive relatively uniform functionality from all data providers."
---

# The Microsoft Cursor Service for OLE DB

When you select a client-side cursor, or set the **CursorLocation** property to **adUseClient**, you are invoking the Microsoft Cursor Service for OLE DB. You might also see references to the "Client Cursor Engine", which is essentially the same thing in the context of ADO. This service supplements the cursor-support functions of data providers. As a result, you can perceive relatively uniform functionality from all data providers. 
  
The Cursor Service for OLE DB makes dynamic properties available and enhances the behavior of certain methods. For example, the **Optimize** dynamic property enables the creation of temporary indexes to facilitate certain operations, such as the **Find** method. 
  
The Cursor Service enables support for batch updating in all cases. It also simulates more capable cursor types, such as dynamic cursors, when a data provider can only supply less capable cursors, such as static cursors.
  

