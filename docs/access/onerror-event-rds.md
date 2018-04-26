---
title: "onError Event (RDS)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e26a3f7f-0f00-919a-65ad-bf39ffb83e92

---

# onError Event (RDS)

The **onError** event is called whenever an error occurs during an operation. 
  
## Syntax

 **onError** *SCode*  ,  *Description*  ,  *Source*  ,  *CancelDisplay* 
  
## Parameters

-  *SCode* 
    
- An integer that indicates the status code of the error.
    
-  *Description* 
    
- A **String** that indicates a description of the error. 
    
-  *Source* 
    
- A **String** that indicates the query or command that caused the error. 
    
-  *CancelDisplay* 
    
- A **Boolean** value, which if set to **True**, that prevents the error from being displayed in a dialog box. 
    

