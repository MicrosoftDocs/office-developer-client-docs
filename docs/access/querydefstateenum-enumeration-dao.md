---
title: "QueryDefStateEnum Enumeration (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: edfa3085-f8b4-b813-0828-2ba2a9dc0b9d
description: "Used with the Prepare property to specify the method used to specify how a query should be prepared."
---

# QueryDefStateEnum Enumeration (DAO)

Used with the **Prepare** property to specify the method used to specify how a query should be prepared. 
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dbQPrepare** <br/> |1  <br/> |(Default) The statement is prepared (that is, the ODBC SQLPrepare API is called).  <br/> |
|**dbQUnprepare** <br/> |2  <br/> |The statement is not prepared (that is, the ODBC SQLExecDirect API is called).  <br/> |
   

