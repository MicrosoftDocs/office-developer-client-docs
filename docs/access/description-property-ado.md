---
title: "Description Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 31df5e36-641c-d213-31fc-6244e2983327
---

# Description Property (ADO)

Describes an [Error](error-object-ado.md) object. 
  
## Return Value

Returns a **String** value that contains a description of the error. 
  
## Remarks

Use the **Description** property to obtain a short description of the error. Display this property to alert the user to an error that you cannot or do not want to handle. The string will come from either ADO or a provider. 
  
Providers are responsible for passing specific error text to ADO. ADO adds an [Error](error-object-ado.md) object to the **Errors** collection for each provider error or warning it receives. Enumerate the **Errors** collection to trace the errors that the provider passes. 
  

