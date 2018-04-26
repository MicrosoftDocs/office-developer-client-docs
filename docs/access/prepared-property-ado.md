---
title: "Prepared Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- ado210.chm1231161
  
localization_priority: Normal
ms.assetid: 33becda2-faab-5000-8904-6ffd8c5805f2

---

# Prepared Property (ADO)

Indicates whether to save a compiled version of a command before execution.
  
## Settings and Return Values

Sets or returns a **Boolean** value that, if set to **True**, indicates that the command should be prepared. 
  
## Remarks

Use the **Prepared** property to have the provider save a prepared (or compiled) version of the query specified in the [CommandText](commandtext-property-ado.md) property before a [Command](command-object-ado.md) object's first execution. This may slow a command's first execution, but once the provider compiles a command, the provider will use the compiled version of the command for any subsequent executions, which will result in improved performance. 
  
If the property is **False**, the provider will execute the **Command** object directly without creating a compiled version. 
  
If the provider does not support command preparation, it may return an error as soon as this property is set to **True**. If it does not return an error, it simply ignores the request to prepare the command and sets the **Prepared** property to **False**. 
  

