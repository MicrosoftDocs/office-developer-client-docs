---
title: "DefinedSize Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 8d6db4c9-fbdc-9fcd-63f0-bd677c5ebcf6
---

# DefinedSize Property (ADO)

Indicates the data capacity of a [Field](field-object-ado.md) object. 
  
## Return Value

Returns a **Long** value that reflects the defined size of a field as a number of bytes. 
  
## Remarks

Use the **DefinedSize** property to determine the data capacity of a **Field** object. 
  
The **DefinedSize** and [ActualSize](actualsize-property-ado.md) properties are different. For example, consider a **Field** object with a declared type of **adVarChar** and a **DefinedSize** property value of 50, containing a single character. The **ActualSize** property value it returns is the length in bytes of the single character. 
  

