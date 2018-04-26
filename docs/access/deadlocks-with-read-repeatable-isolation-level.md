---
title: "Deadlocks With Read Repeatable Isolation Level"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 3d5f3293-33bb-cf6d-362a-278f9ec1bd3c
description: "If a custom business object uses an isolation level of read repeatable to access a SQL Server, and the business object is called simultaneously by two clients that send a query and update in the same transaction, a deadlock is possible. Remote Data Service is designed to allow one of the processes to time out to release the deadlock, but the update will fail for that client."
---

# Deadlocks With Read Repeatable Isolation Level

If a custom business object uses an isolation level of read repeatable to access a SQL Server, and the business object is called simultaneously by two clients that send a query and update in the same transaction, a deadlock is possible. Remote Data Service is designed to allow one of the processes to time out to release the deadlock, but the update will fail for that client.
  
Use the [Cursor Service ](microsoft-cursor-service-for-ole-db-ado-service-component.md) **Command Time Out** dynamic property to modify the length of the timeout. 
  

