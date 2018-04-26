---
title: "Microsoft OLE DB Persistence Provider (ADO Service Provider)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 22e41769-36eb-5a88-05ed-870938657624
description: "The Microsoft OLE DB Persistence Provider enables you to save a Recordset object into a file, and later restore that Recordset object from the file. Schema information, data, and pending changes are preserved."
---

# Microsoft OLE DB Persistence Provider (ADO Service Provider)

The Microsoft OLE DB Persistence Provider enables you to save a [Recordset](recordset-object-ado.md) object into a file, and later restore that **Recordset** object from the file. Schema information, data, and pending changes are preserved. 
  
You can save the **Recordset** in either the proprietary Advanced Data Table Gram (ADTG) format, or the open Extensible Markup Language (XML) format. 
  
## Provider Keyword

To invoke this provider, specify the following keyword and value in the connection string.
  
```
 
"Provider=MSPersist" 

```

## Errors

The following errors issued by this provider can be detected in your application.
  
|**Constant**|**Description**|
|:-----|:-----|
|E_BADSTREAM  <br/> |The file opened does not have a valid format (that is, the format is not ADTG or XML).  <br/> |
|E_CANTPERSISTROWSET  <br/> |The **Recordset** object saved has characteristics that prevent it from being stored.  <br/> |
   
## Remarks

The Microsoft OLE DB Persistence Provider exposes no dynamic properties.
  
Currently, only parameterized hierarchical **Recordset** objects cannot be saved. 
  
For more information about persistently storing **Recordset** objects, see [Recordset Persistence](more-about-recordset-persistence.md).
  
When a stream is used to open a **Recordset**, there should be no parameters specified other than the  *Source*  parameter of the **Open** method. 
  

