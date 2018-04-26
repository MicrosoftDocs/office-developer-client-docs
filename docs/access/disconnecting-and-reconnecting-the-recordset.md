---
title: "Disconnecting and Reconnecting the Recordset"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: d608d95d-9a4e-17a1-107a-b88b77f3774c
---

# Disconnecting and Reconnecting the Recordset

## Disconnecting and Reconnecting the Recordset

One of the most powerful features found in ADO is the capability to open a client-side **Recordset** from a data source and then  *disconnect*  the **Recordset** from the data source. Once the **Recordset** has been disconnected, the connection to the data source can be closed, thereby releasing the resources on the server used to maintain it. You can continue to view and edit the data in the **Recordset** while it is disconnected and later reconnect to the data source and send your updates in batch mode. 
  
To disconnect a **Recordset**, open it with a cursor location of **adUseClient**, and then set the **ActiveConnection** property equal to  *Nothing*  . (C++ users should set the **ActiveConnection** equal to NULL to disconnect.) 
  
We will use a disconnected **Recordset** later in this chapter when we discuss **Recordset** persistence to address a scenario in which we need to have the data in a **Recordset** available to an application while the client computer is not connected to a network. 
  

