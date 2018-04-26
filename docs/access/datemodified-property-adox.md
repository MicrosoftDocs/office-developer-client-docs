---
title: "DateModified Property (ADOX)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: aebe8818-82e7-84a4-24d7-d97afa32e193
---

# DateModified Property (ADOX)

Indicates the date the object was last modified.
  
## Return Values

Returns a **Variant** value specifying the date modified. The value is null if **DateModified** is not supported by the provider. 
  
## Remarks

The **DateModified** property is null for newly appended objects. After appending a new [View](view-object-adox.md) or [Procedure](procedure-object-adox.md), you must call the [Refresh](refresh-method-ado.md) method of the [Views](views-collection-adox.md) or [Procedures](procedures-collection-adox.md) collection to obtain values for the **DateModified** property. 
  

